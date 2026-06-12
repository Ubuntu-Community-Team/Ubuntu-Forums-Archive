---
title: "Download Open Office 3.0 in Hardy ?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-01-23
What do I need to do to replace Open Office 2.4 with a download of Open Office 3.0 ?

---

### Post by stchman on 2009-01-23
> **CoCoKnots said:**
> What do I need to do to replace Open Office 2.4 with a download of Open Office 3.0 ?

You are in luck, I have a script that will uninstall OO2.4 and install OO3 in 32 bit Hardy.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Scroll down to the Scripts section.  Note:  you must have a functioning JRE on your install for all OO3 features to work.

---

### Post by taurus on 2009-01-23
You can download the .deb version.

[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

---

### Post by davideotape on 2009-01-23
If you follow the easy to follow steps here:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

you should have 3.0 up and running in no time. This will automatically replace 2.4 for you.

Hope that helps :D

---

### Post by philinux on 2009-01-23
Add this line to your sources list.

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

Then let update manager do it's job.

---

### Post by Technoviking on 2009-01-23
Add the following ppa to your *System --> Administration --> Software Source --> Third Party Software* list.

```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
```

Then update
```
sudo apt-get update
sudo apt-get dist-upgrade
```

This should install OpenOffice 3.0.1rc1 on Hardy.

Remember,
Always be careful using third party Ubuntu repos, they can install poorly built software that can make your ***system unstable and kick your cat***. Although the OpenOffice Scribblers team PPA is pretty safe. 

T-V

---

### Post by CoCoKnots on 2009-01-23
Please consider this thread [SOLVED]! This worked GREAT... Thanks everyone. And Technoviking, Great, clear instructions. Thanks Again, Cal

---

