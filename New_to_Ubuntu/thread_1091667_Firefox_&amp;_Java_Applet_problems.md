---
title: "Firefox &amp; Java Applet problems"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Wicked_Newb on 2009-03-09
Dear Forumites, 

Can anybody help me with this issue.. I've been attempting to tackle it... unfortunately I think I am 100 points shy of Newbie Status and reside in the wannabe Newbie category.

I am trying to use a website that has applets. However... not working. The applet initializes and starts. Then all of a sudden the display is cropped so I can only see half of the page. I click on one of the links and it stalls completely. 

Finally I get so frustrated I close it down. Now in every Firefox window anything I type comes out mirrored (ie... mirrored looks like derorrim). Annoyed I close down firefox and try to open another. Firefox is still up. I have to go into the System Monitor to shut it down. 

It is not the site's problem as it works fine on machines running 
Windows Vista, Windows XP and Ubuntu 8.04. 

Can anybody help me?

---

### Post by Kareeser on 2009-03-09
Odd. What java add-on do you have installed?

In firefox: Click Tools -> Add-Ons, and list the Java plugin. It maybe called "IcedTea"

---

### Post by Wicked_Newb on 2009-03-09
I have three listed:
IcedTea 
GCJ 0.96.1
Java 1.6.0_10-b33

I Disabled IcedTea as per other threads recommendation. Without it the applet doesn't load. 

I also noticed that in the Sun Java 6 is listed as installed in the package manager but not in the Firefox- Tools>Add-On menu 


Also I noted in the Error Console Regarding the website I am loading from:

Warning: The stylesheet [http://rhi.skillport.com/skillportfe/stylesheets/cf_stylesheets.cfm](http://rhi.skillport.com/skillportfe/stylesheets/cf_stylesheets.cfm) was loaded as CSS even though its MIME type, "text/html", is not "text/css".
Source File: [http://rhi.skillport.com/skillportfe/home/index.cfm?selectedTab=0&myplan=1&myfavorites=0&myreport=0&companyNews=0&shortcut=1&pathInfo=%2F%5FMyPlan%2Fu756567%2FCertificationView%5FenUS%2FCV%5FS1A75733%5FenUS%2FCV%5FS1A75602%5FenUS%2FCV%5FS1A363%5FenUS&rpathinfo=%2FSkillSoft%2FenUS%2FCertificationView%5FenUS%2FCV%5FS1A75733%5FenUS%2FCV%5FS1A75602%5FenUS%2FCV%5FS1A363%5FenUS&origin=mgr](http://rhi.skillport.com/skillportfe/home/index.cfm?selectedTab=0&myplan=1&myfavorites=0&myreport=0&companyNews=0&shortcut=1&pathInfo=%2F%5FMyPlan%2Fu756567%2FCertificationView%5FenUS%2FCV%5FS1A75733%5FenUS%2FCV%5FS1A75602%5FenUS%2FCV%5FS1A363%5FenUS&rpathinfo=%2FSkillSoft%2FenUS%2FCertificationView%5FenUS%2FCV%5FS1A75733%5FenUS%2FCV%5FS1A75602%5FenUS%2FCV%5FS1A363%5FenUS&origin=mgr)


Not sure if this is related or not... 
Line: 0

---

