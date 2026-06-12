---
title: "How to run crystal reports in ubuntu"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by srikantmatihali on 2009-11-23
Hi all,

I am very new to Ubuntu. I want to deploy .net application in ubuntu.

So far i was able to install wine as well as trial version of crossover. And in Crossover i was able to run small .net application (developed in xp environment and deployed as .exe) which uses mysql database.

**Please check the below links**

[http://stackoverflow.com/questions/1781229/how-to-run-crystal-reports-in-ubuntu-linux](http://stackoverflow.com/questions/1781229/how-to-run-crystal-reports-in-ubuntu-linux)

[http://www.talkonsomething.com/2009/11/how-to-connect-mysql-database-from-windows-xp-to-ubuntu/](http://www.talkonsomething.com/2009/11/how-to-connect-mysql-database-from-windows-xp-to-ubuntu/)

I was even able to display static crystal reports with labels in it. 

I was not able to connect to mysql database and fetch data from it and display it through crystal reports. But i was able to generate mysql data on datagridview using forms.

---

### Post by srikantmatihali on 2009-11-23
Hi all, 

I was expecting a faster reply from the moderators but, I got the answer by my own after doing a small research. Hope this would be helpful. 

The error was due the licensing problem of visual studio .net 2005. The following packages had to be configured in Merge Reports (i.e C:\Program Files\Common Files\Merge Modules)

Crystal_Managed2003.msm
Crystal_Database_Access2003.msm
Crystal_Database_Access2003_enu.msm
Crystal_regwiz2003.msm

And then we need to enter the license key while deploying the application correctly.

Later the following packages would be installed automatically when we run the deployed .net application in ubuntu linux

Refer screenshot below

[IMG]http://i49.tinypic.com/ohocns.png[/IMG]

---

