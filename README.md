## data-512-a1: DATA 512 Assignment 1

### __About Project__  

  The goal of this project is to follow best practices for open scientific research while constructing, analyzing,  
  and publishing a dataset of monthly traffic on the pages in English Wikipedia from July 1, 2008 through Sept. 30, 2017.  
  The resulting project should contain enough information to be fully reproducible by others:  
  from data collection to data analysis.  

  This project documents:  
  > (1) the code to combine Wikipedia traffic data from two Wikimedia REST APIs into a single dataset,  
  > (2) the data wrangling steps necessary to consolidate five JSON files into a single CSV file, and  
  > (3) the visual analysis of the formatted data.  

  This README file and the Jupyter Notebook file, hcds-a1-data-curation.ipynb, contain the information and  
  references needed to reproduce the analysis, including a description of the data and all relevant resources  
  and documentation, with hyperlinks to those resources.  
  
### __About Data__

#### Copyright
The Wikipedia data was gathered from the Wikimedia REST API, Wikimedia Foundation, 2017. CC-BY-SA 3.0  

#### License
This Wikimedia Foundation data is licensed under an Apache 2.0 License, which includes in part:  

> Unless required by applicable law or agreed to in writing, software  
> distributed under the License is distributed on an "AS IS" BASIS,  
> WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  
> See the License for the specific language governing permissions and  
> limitations under the License.  

For more information on the this license, see [Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0).

#### Terms of Use
For information on Wikipedia's terms of use, see the Wikimedia Foundation terms of use [LINK](https://wikimediafoundation.org/wiki/Terms_of_Use/en). 

### Sample Visualization of Data
![alt text](https://raw.githubusercontent.com/orbitse/data-512-a1/master/WikipediaDataPlot_Std.png)  
This visualization of the Wikipedia page view data was created with matplotlib and without the Seaborn style.  
See the Jupyter Notebook file, hcds-a1-data-curation.ipynb, for the instructions on how to create this visualization.

### __API Documentation__
 
The Wikipedia page view data used in this project came from two APIs: Pagecounts API and Pageviews API. 

 - __Pagecounts API__ ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)) provides access to desktop and mobile traffic data from January 2008 through July 2016.  
 This, older, legacy Pagecount API does not allow you to filter by user, so the monthly counts include all  
 the views by people, bots, and webcrawlers.  

 - __Pageviews API__ ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through September 2017.  
 The Pageview API gives you the ability to exclude traffic from spiders and crawlers, by setting the  
 agent parameter to agent = user.  
 
The above documentation explains the parameters you can set. For example, both the Pageview and Pagecount APIs allow  
you to get data on page views of other Wikipedia pages if you don't want the views of all English Wikipedia pages.  

For additional information about how the APIs were used, see the Jupyter Notebook file, hcds-a1-data-curation.ipynb.
 
### __Other Tools__

In addition to the APIs described above, the Jupyter Notebook file in this repository, hcds-a1-data-curation.ipynb,  
contains the python code to get, parse, save, consolidate, and visualize the data.  

Jupyter Notebook is an open-source web application for viewing and distributing code.  
To install Jupyter Notebook or review documentation, visit https://jupyter.org.  

You will need python 3.X and the following python libraries to run the code in hcds-a1-data-curation.ipynb.  
  - [matplotlib](https://matplotlib.org) : will be used for data visualization
  - [pandas](http://pandas.pydata.org) : will be used for data processing
  - [seaborn](http://seaborn.pydata.org) -- Note: this library is only for style purposes and is not essential
  
  If necessary, you can pip install any of the above libraries, for example:  
  `pip install requests` or `pip3 install requests`.  
  Additionally, if you have any version of python 3.X installed, you should already have the csv, json,  
  and requests dependency libraries installed. These libraries will be used to get and save data in notebook  
  file, hcds-a1-data-curation.ipynb. 

### Final CSV Data File: en-wikipedia_traffic_200801-201709.csv  

The columns in the final, consolidated CSV file include: year, month, pagecount_all_views, pagecount_desktop_views, pagecount_mobile_views, pageview_all_views, pageview_desktop_views, and pageview_mobile_views.  

 - pagecount_all_views = pagecount_desktop_views + pagecount_mobile_views
 - pagecount_desktop_views: monthly views of the main English Wikipedia pages  
   from Jan. 2008 - July 2016
 - pagecount_mobile_views: monthly views of the mobile version of the English Wikipedia  
   pages from. Jan. 2008 - July 2016
 - pageview_all_views = pageview_desktop_views + pageview_mobile_views
 - pageview_desktop_views: monthly page views by users rather than bots or web crawlers  
   of the main English Wikipedia pages from July 2015 \- Sept. 2017
 - pageview_mobile_views: monthly page views by users of both the mobile English Wikipedia  
   pages and via the mobile app from July 2015 \- Sept. 2017  
