---
title: "moneydance"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by budd2light on 2010-04-18
I have been unable to open "Moneydance" in Ubuntu Linux. I have installed and reinstalled the program, but I always get "illegal option -p" when I try to invoke the program. I am a Linux newbie and I cannot find any reference in the texts that I have to "option -p". The help facility at Moneydance has been quite reponsive, but still unable to get me past this roadblock.
                                bud light

---

### Post by oldfred on 2010-04-18
Welcome to the forums.

Are you launching from the applications menu or command line. I do not have moneydance.

You can see the applications menu settings with a right click on applications and edit menus. Find the category (office) for moneydance and click on it and you can view properties.

You can usually launch programs with the same commands as shown under the properties ( may just be moneydance but some programs have totally different names to launch) above or modify command to test alternatives. With command line you then will see any error or warning messages to help solve problems.

---

### Post by lkraemer on 2010-04-20
When you downloaded Moneydance you downloaded a file named as:
Moneydance_linux_x86.tar.gz      Let's assume you downloaded it to
your /home/user/Downloads folder.

Note: Java has to be installed

I copied mine to /home/user/Moneydance

You double left click on the tar.gz file to extract the Moneydance
folder.  I have mine at /home/user/Moneydance/Moneydance

In this folder there is a file named Moneydance with the following
permissions:
-rwxr-xr-x Moneydance   (as shown in a Terminal window with the
command:
ls -alt )

For you to get here Open a Terminal Window and type the following:
Copy & Paste to prevent errors.....Look for the PERIOD  in the 4th line
below......
```

pwd
sudo mkdir Moneydance
cd Moneydance
sudo cp /home/user/Downloads/Money* .
ls -alt
cd Moneydance
ls -alt
./Moneydance

```
Or you can use PLACES -> HOME FOLDER _> Moneydance -> Moneydance
to get to the file.  Double Left click on it to run it.  Click on
Execute.  Moneydance should start.

Good Luck.


If you want to uninstall the Demo version:
From: Ben Spencer
Subject: how to Uninstall in Ubuntu 8.04 after trial period 

Being a java application Moneydance is relatively self contained. All 
data related to moneydance will be stored in only 2 folders. There is 
the moneydance directory which contains the applcation and the is a 
hidden folder in your users home folder called .moneydance. Deleting 
these two folders will completely remove the application from your 
system.

My recommendation for installing Moneydance on ubuntu 8.04 is to install 
the latest version of java from sun using the synaptic package manager. 
The package name is "sun-java6-jre" without the quotes. And then 
download Moneydance from here:

[http://moneydance.com/other](http://moneydance.com/other)

Clicking on the link that says "Linux (x86 processor, does not include 
Java)"

I recall there being some incompatibility problems between java and 
compiz fusion in ubuntu 8.04. This resulted in some popup windows 
occasionally being blank. This sun fixed this in later releases of java 
and I am not sure if the fix got back ported to 8.04. If you experience 
this problem turning off desktop special effects resolves the issue. 

Sincerely

Ben Spencer

View this Discussion online: 
[http://help.infinitekind.com/discussions/questions/559-how-to-uninstall-in-ubuntu-804-after-trial-period](http://help.infinitekind.com/discussions/questions/559-how-to-uninstall-in-ubuntu-804-after-trial-period)


lk

---

