# Smart Data Processing

This notebook is a step-by-step guide on how to process and convert the Generation Data provided by SMARD.
The Data is converted into yearly perUnit Genration Data, similar to the ENTSO-E per Unit Generation Data.

The processed Data can be downloaded already, it is saved in the _output_ folder. 

## Download
The downloaded data is already included in this repo, but for understanding it is described how the data was downloaded.

Therefore the data was downloaded for each year from _2016-2021_ via the SMARD Website:
https://www.smard.de/home/downloadcenter/download-kraftwerksdaten/
As settings for the download was chosen:
- As language for the Website choose _Deutsch_ as the names for Units in the CSV Files can differ when downloaded with _English_ as language setting.
- __Alle Kraftwerke__
- __Inhalt: Realisierte Erzeugung__
- Datums: __01.01.Year - 31.12.Year__ where _Year_ is replaced by each year 
- __Originalauflösung__
- __CSV__

The Data downloaded will be provided as a zip-folder. In order to run the code correctly, __all__ CSV-Files in the ZIP Folder have to be copied into the _input/smard_ folder. This has to be done for each year independently, where in the end all Files downloaded are in the _input/smard_ folder. 

### Note to the download
The dowload might take a bit to start, as the query is first processed by the SMARD Website and then the wanted csv-files are generated and packed into the ZIP Folder. __Important__ to know is that the download was invalid if the name of the zip-folder is _export.zip_. It can happen, if so try again. The folder name has to be something like _Tabelle-Daten_ or _Table-Data_.

## Processing
In the SMARD Date each Power Plant has their ow CSV-File, where the Power Plants listed come from the _Bundesnetzagetur_. In these CSV Files exists one column per Block, but not named consitently, which makes an automated matching of _EIC-ID_ and column difficult.
Therefore a xlsx Table called _blocks.xlsx_ is used to process the Data, in which each block is listed with _EIC-ID_,_ETS-ID_, _Block Name_ and corresponding _filename_ as well as _Column Name_ in the smard Data. The _blocks.xlsx_ can be found in the input folder and was created by the INATECH Team.

With the _blocks_ Data the Data is processed and Converted in a way that each ETS-ID has their own file, named in the following pattern __{Plant Name}_{ETS_ID}_{Year}__, which makes it way easier to process afterwards. In these CSV Files the columns are Named with the EIC ID, which provides a consistend naming and good processing.

The Notebook shows how exactly the Data is processed and can be used to understand the method. As well the Processed Data is already available for downloaded, saved in the _output_ Folder.

# License 
Data provided from SMARD is Licensed under Creative Commons 4.0