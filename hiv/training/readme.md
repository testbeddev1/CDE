This information will be part of Research tab at AIDSInfo (https://aidsinfo.nih.gov/research)

Two sections are below: for investigator and for data re-using reseachers

# Study investigator 

## Set of recommendations:
-	Provide data dictionary documentation separate from de-identified individual participant data. Since it contains no participant level data, do not require local ethical approval as a condition of releasing the data dictionary (no request-wall).
-	Utilize ClinicalTrials.gov fields for uploading study protocol, empty case report forms, statistical analysis plan and link to 
    -	Example trial: https://clinicaltrials.gov/ct2/show/NCT00923936
-	Provide basic summary results using results registry component of Clinicaltrials.gov
-	Share Case Report Forms in non-PDF, machine readable format. For example, REDCap, OpenClinica and several other Electronic Data Capture (EDC) systems allow export into CDISC Operational Data Model (ODM) format for forms. If no cross-platform standard is supported by your EDC, provide CRFs in the platform-specific format. 
-	If you considered formally defined research Common Data Elements at study design (more common for studies initiated after 2015), provide a spreadsheet file that lists all CDEs utilized by your study. Include unique CDE identifies (e.g., PhenX VariableID).  
-	Use data formats that can be natively loaded (without add-ons) into multiple statistical platforms (e.g., prefer comma/tab separated values (.CSV) files to SAS XPT, XLS/XSLX) 

 
-	Distinguish string field with free text from string field (with a set of permissible values)
-	For pick list questions, provide in data dictionary the options that are possible
    


# Data re-using reseacher

Note: CT.gov evaluates some numeric blank codes (9999999) as being legal enrolment amounts. 
Ask: It is highly unlikely that there are 10 million people in any of these trials. CT.gov should handle this better; either by using logic-range checks to replace large enrollment values or consider using upload rules for SAS, SPSS, STATA and RedCap numeric item responses so that they map to ‘blank’ values. 

Note: CT.gov has several methods for describing HIV and AIDS including key words, mesh terms and study conditions. These methods return contradictory results including trials that can only be discovered by one method above.
Ask: CT.gov should use one and only one index method. Free ‘string’ descriptions should be banned as they say more about the trial intent rather than the re-use value of the records described. 

Note: There are several places in PubMed XML, Medline and the web interface where a clinical trial can be declared. Investigators populate this in a very catch as catch can way. There are too many searchable fields where a publication can describe itself as a clinical trial. These are seldom fully populated and different searches reveal different trial volumes.
Ask: PubMed should use one and only one method for declaring a paper a clinical trial 

Note: PubMed does not have a single method for stating an NTC-ID. Discovering these ids is not hard, but finding them all for a given search criteria is quite difficult.  
Ask: PubMed should use one and only one location for an NTC ID. 


Note: Data sets should not be output as XLS; which is problematic for large files and files where complex characters are used (drug names). XLS also passes the problem of data management down to the next user instead of solving it outright.  
Ask: CSV with header and quoted strings is ideal.

Note: Drug names are complex alias features for several well-known reasons. Files that describe drug names should standardize them in a functional way. For example |Asprin|mg|50 shows a drug name,  measure and amount; ‘ASPRINMG50’ is not machine or human readable... 
Ask: Drug names should be human and machine readable. Ideally the dosage and measure for the dosage should be stored separately for analysts to integrate on their own. 

Note: Metric is CASE SENSATIVE! Common usage, not explicit usage make drug amounts easy to understand; however inaccurate. For example MEGA-GRAM is Mg, not milligram which is just mg (downcase). There is a one million fold difference between G (gram) and MG. 
Etymology
mega- +‎ gram 
Noun
megagram (plural megagrams) 
1.	A unit of mass equal to 1,000,000 grams. Symbol: Mg 
Synonyms: metric ton, tonne

milligram (plural milligrams) 
1.	An SI unit of mass, equivalent to one thousandth of a gram. Symbol: mg

Ask: Write out the whole word in a standard way; or declare MG as milligram in a data dictionary. I don’t think one million grams (one metric ton; let alone 50) was prescribed as aspirin to a human (or any animal for that matter). International data integration will be confounded by this. Also electronic record systems will output M, mg and MG depending on where they are populating from; further complicating data integration in a machine to machine context. 

Note: Some data sets uses concept codes to fit disparate yet identical concepts to a consistent, cross study framework. This is wonderful but it makes comparing in-house to out-of-house data difficult when all of the data harmonization efforts that the data vendor has undertaken are vended data specific. 

Ask: Consider standard data formats (OMOP works) and the distance between your internal data standard and common ones. The difficulty of transformation to a common standard should be considered before you commit to an internal data standard. 

Note: ICD-10 and ICD-9 denominated records are common issue in our moment; especially with historic samples. Seldom will data providers declare if their ICD-9 codes are ICD-10 ‘roll downs’ or if their ICD-10 codes are ICD-9 ‘roll ups’. 
Ask: Include a column where the coding system the data was collected in is declared row wise with the code itself. Ie: Collected as/ICD-9CM|ICD-10 Event/ICD-10 code. Here we can see which records are rollups, roll downs and we can make decisions about concept integrity more easily. 

Note: Data analysis requires one-procedure-per-column at one person-per-row or tidy format. EKG, PFT and ECHO files are not tidy. Individual procedure item responses for individual patients cost several rows. While this may be helpful for data storage and transport this is not an analysis format.  Further the procedures files include demography file values; this is inefficient and may be unnecessary. 
Ask: Either de-nest procedures for analysis use cases and provide a script or guidance on best practices for analysts for how to handle this problem. 	

Note: Observational notes, some codes and ‘home made’ concepts include restricted use characters like punctuation (especially commas). 
Ask: Data hosts should clean their text responses and dictionaries as to remove any punctuation that will cause truncation issues before vending data.  

Note: Long text responses are irregular and are not well handled; especially observation notes.
Ask: If you include blob text responses, please write them as the last variable in a text file and be sure to quote them at write out. If they tunicate and you write the column last we only lose one column. If you put the blob first, you lose the whole truncated record. 

Note: Time functions are complicated because there are many, many ways to store and parse them. Most programs use a different method.
Ask: please declare time in an itemized way to ease analysis. For example, storing year, day and month of event as three columns is ideal in a transport format as the analyst can concatenate dates and times at will without managing parsing // or --. Times should not be stored in the date field either. 

Note: Study time frames contain events that occur in PT life cycles. Calculating 'days old at event’ is not only helpful for analysts but easily done. 
Ask: Along with date formats, which vary by location and facility please consider calculating days old at event for each event described in your data set if you insist on using nested time statements. 

## Lessons learned from requesting data from various platforms

### Vivli



