---
title: "How to install freerapid downloader"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by djftl on 2010-09-14
Hi there, 

I just downloaded Vity's freerapid Downloader and I'm struggling to install it. I'm running Ubuntu 9.04 and I have installed java version "1.6.0_20". The readme txt installation notes are not working for me.

Readme txt: Installation
------------
Unzip files to any of your directory, but beware special characters (like '+' or '!') on the path.
If you make an upgrade to higher version, you can delete previous installation folder. All user
settings are preserved, but it's recommended to backup them.
All user settings are saved in home directories:
MS Windows: c:\Documents and Settings\YOUR_USER_NAME\application data\VitySoft\FRD
            
Linux: ~/.FRD

DO NOT copy new FRD version over older one.

How to get the latest Sun Java on Linux (Ubuntu)?

Run these commands:
- apt-get update
- apt-get install sun-java6-jre
- update-java-alternatives -l
- update-java-alternatives -s java-6-sun

Launching
-----------
Windows
 Simply launch frd.exe


Linux
 Run command ./frd.sh
 (as first put correct executable rights on this file )


All platforms
 Run command java -jar frd.jar.
-------------------------------------


I extracted my files to my documents folder. When I sudo and type that address example: /home/djftl/Documents/FRD/FreeRapid-0.83u1/frd.sh- it says command not found.

Anyone knows how to install it.

Thanks in advance.

Regards,

Tobela

---

### Post by themusicalduck on 2010-09-15
The easiest way to run a .sh file is by using "sh".

So in your case you would use ```
sh /home/djftl/Documents/FRD/FreeRapid-0.83u1/frd.sh
``` or if you need to run it as sudo then just "sudo sh /home/djftl/Documents/FRD/FreeRapid-0.83u1/frd.sh"

Also, make sure you give it executable rights first (as it says on the readme you posted) you can do this with ```
sudo chmod +x /home/djftl/Documents/FRD/FreeRapid-0.83u1/frd.sh
``` or just right click the file and look on the Permissions tab.

---

### Post by DarkBattM14 on 2011-12-05
Ohhh.. Thank you... this is a good downloader.. :popcorn::popcorn:

---

### Post by gandaran on 2011-12-05
> All platforms
Run command java -jar frd.jar.
**java -jar frd.jar** is the correct way to run java applications 
but on ubuntu you can run the application even easier, just right click on the **frd.jar** file and choose from the menu to open with either sun-java or openjdk-java 
check that you have sun-java installed if the application wont work with openjdk-java

---

