---
title: "Problem with Python script"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by blues2use on 2009-10-13
If I click on Places/Home Folder then browse to my linuxvideoconverter folder and double-click the linuxconverter script file there, a dialog box opens and "**Do you want to run "linuxvideoconverter", or display its contents?**" is at the top and and **Run in Terminal**, **Display**, **Cancel** and **Run** are options in the dialog box at the bottom...

If I choose **Run**, the script runs and it works just fine...

So, I look for my python:

bob@ubuntu:~$ which python
/usr/bin/python

Here's what I get running from the terminal:

bob@ubuntu:~$ linuxvideoconverter
bash: linuxvideoconverter: command not found

Here's my path:

bob@ubuntu:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/
home/bob/dirkdashing

Does /usr/bin/python have to be in my path? I have other Python scripts installed and running without problems...

**btw** - I can't figure out how to get rid of **/home/bob/dirkdashing**...I installed the game for the grandson a good while ago and then removed the game...

**Thanks in advance for the help**


Okay, I fixed it. I tracked down all of the files from the original installation package (a .gz version) and got rid of them. Then I downloaded the noarch RPM version and used alien to convert to a .deb and installed. The executable then showed as /usr/bin/linuxvideoconverter and works just fine via my menu item in Applications/Sound & Video.

---

### Post by blues2use on 2009-10-13
> **blues2use said:**
> If I click on Places/Home Folder then browse to my linuxvideoconverter folder and double-click the linuxconverter script file there, a dialog box opens and "**Do you want to run "linuxvideoconverter", or display its contents?**" is at the top and and **Run in Terminal**, **Display**, **Cancel** and **Run** are options in the dialog box at the bottom...

If I choose **Run**, the script runs and it works just fine...

So, I look for my python:

bob@ubuntu:~$ which python
/usr/bin/python

Here's what I get running from the terminal:

bob@ubuntu:~$ linuxvideoconverter
bash: linuxvideoconverter: command not found

Here's my path:

bob@ubuntu:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/
home/bob/dirkdashing

Does /usr/bin/python have to be in my path? I have other Python scripts installed and running without problems...

**btw** - I can't figure out how to get rid of **/home/bob/dirkdashing**...I installed the game for the grandson a good while ago and then removed the game...

**Thanks in advance for the help**

Sorry...should have stated that I am trying to run from Applications/Sound & Video by adding a new menu item...I followed the same steps that I have used in the past. If I try to execute from here, nothing happens at all...no errors...no indication of anything trying to load. That is what originally prompted me to drill to the script location and execute it from there.. and it works if I do that.

**Thanks**

---

### Post by ConXtionS on 2009-10-13
Wow... way above my head....
 
Im not trying to help here... but if you dont mind, what is linuxvideoconverter please???>?  It sounds like something I might want to break... um I mean PLAY WITH until my computer smokes again...
 
Welcome to Linux
 
Jim

---

### Post by blues2use on 2009-10-13
> **ConXtionS said:**
> Wow... way above my head....
 
Im not trying to help here... but if you dont mind, what is linuxvideoconverter please???>?  It sounds like something I might want to break... um I mean PLAY WITH until my computer smokes again...
 
Welcome to Linux
 
Jim

Jim,

Here you go....

Name: linuxvideoconverter
Version: 0.9.1
Summary: A simple video converter
Home-page: [http://rudd-o.com/new-projects/linuxvideoconverter](http://rudd-o.com/new-projects/linuxvideoconverter)
Author: Manuel Amador (Rudd-O)
Author-email: [email]rudd-o@rudd-o.com[/email]
License: GPL
Description: Linux video converter simplifies conversion of videos to different formats.

Let me know if it works for you...

---

### Post by blues2use on 2009-10-13
> **blues2use said:**
> Sorry...should have stated that I am trying to run from Applications/Sound & Video by adding a new menu item...I followed the same steps that I have used in the past. If I try to execute from here, nothing happens at all...no errors...no indication of anything trying to load. That is what originally prompted me to drill to the script location and execute it from there.. and it works if I do that.

**Thanks**

Okay, I fixed it. I tracked down all of the files from the original installation package (a .gz version) and got rid of them. 

Then I downloaded the noarch RPM version and used alien to convert to a .deb and installed. 

The executable then showed as /usr/bin/linuxvideoconverter and works just fine via my menu item in Applications/Sound & Video.

I had forgotten about using alien to convert a noarch RPM to a deb file and (usually) getting a good install... :oops:

---

