## Front page
- Hi, all.  
- I am Benny Chin, a PhD student from Department of Geography at National Taiwan University.  
- I am here to present a web-based framework for monitoring spatial temporal clustering of epidemics in Taiwan.   
- This monitoring framework is a prototype of an earlywarning system, with the database of foodborne disease.

- This project is supported by the grant of the CDC Taiwan. 

## about Taiwan
- Taiwan is an island at East Asia. The population density is about 650 person per km. It is one of the top ten most densely populated countries. 

## about foodborne disease
- foodborne disease, is about the illness that when we ate something that is not clean, 
- which made us feeling stomachache (acute diarrhea)
- then we might run to toilets,
- and we might go to the hospital or nearby clinic, to get some medicine.


### how can GIS help
- this is an example
- one day, someone goes out from his home
- takes his lunch (where he ate some not clean food)
- meets with some friends and watches a movie
- then he feels sick (with his stomach) and finally he goes to hospital 

The whole process includes a lots of movement, which we did all the time in our daily life.
- If there is a source that is causing the foodborne disease, 
- there would be a lots of people getting similar symptom in the same area or the neighboring area
- with the helps from GIS and spatial analysis methods, we could find the source of the foodborne disease.

### surveillance system
- so, this is what we are trying to do here.
- the hospitals record the symptoms of patients, they have the summary of the number of patients with a particular symptom, and we know where the hospitals are located. 
- therefore, we could trace back to the source of the foodborne disease. 

## the databases
In Taiwan, the cdc provides several surveillance system and database that could be used in the framework.
- The RODS, LARS, and reporting system
- the report time of RODS is real-time or near real time, but the records would only be the symptoms, without more details information.
- LARS would have about 5 to 10 days lag. but they will also provide the experiment result of the sample, which includes the pathogens type that is causing the disease.
- reported clusters will be announced while the clusters are confirmed, which would have quite detail test results.

### reporting time
- RODS is a better option for surveillance purpose
- LARS is good for supporting the surveillance purpose
- Reporting system is good for verifying the cluster

## the framework
has several components:
- a core system that "control" the workflow
- a database that stores the raw data and result of the analysis
- several analysis modules that "run" the analysis and store the data back to the database
- a web-based UI for communicating with the authorized users.

### core system
- we used a web-application framework name web2py, which is an open-source python-based web application, to construct a dynamic website for the surveillance framework.
- web2py use a MVC structure
- it is a simple and powerful enough web-application for our monitoring system.

### the database
- we used postgresql, with psycopg2 for connecting from python environment
- to store raw data, the number of patients in each day...
- to store spatial data, the locations of the hospitals, the administrative boundaries...
- to store analysis result, where the clusters are...

### analysis modules
- clustering methods
- spatial manipulations
- visualizations

### web-based UI
- html forms...
- showing maps
- showing charts

## warning workflow
- first, analyzing the temporal anomaly from the RODS data, give a warning signal if temporal anomaly appear.
- second, identifying the space-time hotspots from the temporal anomalies, give a warning alert if hotspot is starting or growing.
- then, integrate with the LARS data, which provide information about which types of pathogens, this helps on identifying the food source.

### temporal anomaly
- is those time-point with higher values of patients than regular
- in this figure
- each dot represent the number of patients in a day at the hospital
- dots in purple means less than 50.
- dots in red means greater than 50.
- three continuous three days starting from about day 7, is higher than other days of the hospital.
- this make them temporal anomalies.


### space-time hotspots
- on the other hand, space-time hotspots analysis try to find space-time hotspot from the temporal anomaly data. 

## screenshots - indexpage
- warning messages
- data update history
- thumbnails and links of the maps and charts

### data exploring pages
- RODS spatial
- RODS temporal
- LARS spatial
- LARS temporal

### identified hotspots temporal
- the lines represent the reported clusters
- dots represents the identified hotspots that classified with the LARS pathogens info - red means rota virus, and blue means salmonella species.

### identified hotspot spatial
- we can view the maps of the hotspot area

### and, the hotspot matrix

### we can also check the historical hotspots and reported clusters, to check if the hotspot is closed to any reported clusters.

## thats all
thank you
