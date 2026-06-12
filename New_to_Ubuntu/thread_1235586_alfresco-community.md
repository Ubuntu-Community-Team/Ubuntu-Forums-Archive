---
title: "alfresco-community"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by morimo on 2009-08-09
I read about alfresco and ubuntu.

I just installed ubuntu 9.0.4 jaunty server. 
Installed LAMP, Tomcat, SAMBA at OS install. 
Used sudo apt-get install alfresco-community to install alfresco.

installation went well no errors. 

opened workspace and everything went well.

when i opened Alfresco Share using admin account i get this error on one of the dashlet.

An error has occured in the Share component: /share/service/components/dashlets/rssfeed.
It responded with a status of 500 - Internal Error.
Error Code Information: 500 - An error inside the HTTP server which prevented it from fulfilling the request.
Error Message: 07080003 Failed to load script '/org/alfresco/components/dashlets/rssfeed.get.js (in classpath store file:/var/lib/tomcat6/webapps/share/WEB-INF/classes/alfresco/site-webscripts)': 07080002 ReferenceError: "XML" is not defined. (file:/var/lib/tomcat6/webapps/share/WEB-INF/classes/alfresco/site-webscripts/org/alfresco/components/dashlets/rssfeed.get.js#150)
Server: Alfresco <unknown> v<unknown> schema -1
Time: Aug 8, 2009 2:04:31 AM

didn't really mind at first just deleted rss dashlet. but when I was making a collaboration page. I run into another error on the wiki and the rest.


An error has occured in the Share component: /share/service/components/wiki/page.
It responded with a status of 500 - Internal Error.
Error Code Information: 500 - An error inside the HTTP server which prevented it from fulfilling the request.
Error Message: 07080021 Failed to load script '/org/alfresco/components/wiki/page.get.js (in classpath store file:/var/lib/tomcat6/webapps/share/WEB-INF/classes/alfresco/site-webscripts)': 07080020 ReferenceError: "XML" is not defined. (file:/var/lib/tomcat6/webapps/share/WEB-INF/classes/alfresco/site-webscripts/org/alfresco/components/wiki/page.get.js#173)
Server: Alfresco <unknown> v<unknown> schema -1


An error has occured in the Share component: /share/service/components/blog/filters.
It responded with a status of 500 - Internal Error.
Error Code Information: 500 - An error inside the HTTP server which prevented it from fulfilling the request.
Error Message: 07080023 Failed to load script '/org/alfresco/components/blog/filters.get.js (in classpath store file:/var/lib/tomcat6/webapps/share/WEB-INF/classes/alfresco/site-webscripts)': 07080022 ReferenceError: "XML" is not defined. (file:/var/lib/tomcat6/webapps/share/WEB-INF/classes/alfresco/site-webscripts/org/alfresco/components/blog/filters.get.js#9)
Server: Alfresco <unknown> v<unknown> schema -1


An error has occured in the Share component: /share/service/components/documentlibrary/documentlist.
It responded with a status of 500 - Internal Error.
Error Code Information: 500 - An error inside the HTTP server which prevented it from fulfilling the request.
Error Message: 07080025 Failed to load script '/org/alfresco/components/documentlibrary/documentlist.get.js (in classpath store file:/var/lib/tomcat6/webapps/share/WEB-INF/classes/alfresco/site-webscripts)': 07080024 ReferenceError: "XML" is not defined. (file:/var/lib/tomcat6/webapps/share/WEB-INF/classes/alfresco/site-webscripts/org/alfresco/components/documentlibrary/documentlist.get.js#41)
Server: Alfresco <unknown> v<unknown> schema -1

My question is what am I missing? 

I thought it was bad install so I did a fresh installl and the same thing.

Thank you in advance.

---

