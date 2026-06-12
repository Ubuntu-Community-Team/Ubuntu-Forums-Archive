---
title: "Reinstalling XP and partitioning for Ubuntu"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by 2blue on 2009-02-12
My computer chrashed badly two weeks ago, and after maaaaany hours of trying to repair and restore I gave up. Luckily I managed to retrieve the most important documents with Puppy Linux. 

Then I figured it would be the easiest to do a clean install of XP top get back to factory settings and functions and then partiton for Ubuntu at the same time. However I have run in to difficulties. 

When reinstalling XP, the recovery CD had to configure (correct term?) filesystem on the harddisk as it stated something was wrong. It took for ever; I went out for a walk and when came back XP was installing its self. All seemed to run along regularly until I booted. Now wireless do not work. It cannot be stared with the button on the laptop-panel (behind the keyboard) an not from control panel either. Icons seems somwhat stretched and I cannot find the settings for this either. I usually have no problem with this. 

Anyhow, I figured I could start with installing Ubuntu and I boot the live CD. Still now wireless network. When I choose to start installing and the partition editor starts it gives some alarming warnings like "file system on harddisk is rapidly deteriorating" and it suggested taking some action I didn't  quite understand, involving windows. 

Then I figured I might have done something very wrong when installing XP and tried to do another installation. But the options I get this time when I rund the recovery CD is warning me of lots of trouble. I cannot install another opertative system on the harddisk that is all ready taken over by the newly installe XP. 

The other option is to first erase the harddisk but when I try to do this I get a warning that goes something like "if harddisk is erased it might not be possible to install XP or boot after wards". 

Any ideas on how to deal with this?

---

### Post by prometheus1981 on 2009-02-12
All I can think of when I read the error, is that if you delete the contents of your HDD, XP will not boot (cause it's not there). You can try formating and reinstalling the two OS's starting with Ubuntu and creating a partition while in the installation so that you can install XP after. If your HDD cannot do this, then maybe you have bad sectors in your HDD and need to get a new one.

---

### Post by Mark Phelps on 2009-02-12
Not being difficult, but you're asking questions that are hard to answer without knowing the contents of the Recovery CD.  Some of these boot to a "hidden partition" and use that to completely restore the entire hard drive.  Others have the restore image on the CD/DVD and do the same kind of restore.  I've had such a restore take over 8 hours -- that,s right, hours!

Others simply boot into Win PE and let you do some recovery utilities -- they don't wipe or install anything, they just do repairs.

Given that your machine crashed suddenly, and now you're getting filesystem-related error messages, that looks a lot like a failing hard drive.

So, what exactly are you able to do at present?

---

### Post by 2blue on 2009-02-12
Hmm, do hard drives go bad? I didn't know that. I have an antique Packard Bell laptop (2001) that runs fines and Ubuntu literally slided on to it, every thing working right away. 

This is my regular laptop a Fujitsu Siemens Amilo, and I really need to get it working again. 

Is there any way to check the harddrive for errors and weaknesses?

---

### Post by 2blue on 2009-02-12
Thank your Mark for the information! Is there anyway to check for how things are done on my computer and on my recovery disk? I have a Fujitsu Siemens Amilo L 1310 G and there are not impressivly much stated on the recovery disk. 

"The software on this recovery CD was pre-installed on the harddisk by the factory and can only be used for recovery and security back-ups on your Fujutsu Siemens Computers. Windows XP Home Edt-SP2". 

This might sound a bit odd since it is written in norwegian, and  my English could be better.

---

### Post by Mark Phelps on 2009-02-12
Hard to answer the question because I'm not clear the state of your laptop at present.  what is installed now? And, what is working now?

---

### Post by 2blue on 2009-02-12
Windows XP SP2 is installed and working to a certain degree, but I'm not able to activate the wireless network at all. There's not much else I have tried running or install. 

Ubuntu will not intall and are not willing to run the partition editor. It seams to run OK as live CD.

---

### Post by mike555 on 2009-02-12
There are live cd's that just test hard drives , I had one , but forgot the name ..... Google will find it ....  something like " HD-test "

---

### Post by Mark Phelps on 2009-02-13
> **2blue said:**
> Windows XP SP2 is installed and working to a certain degree, but I'm not able to activate the wireless network at all. There's not much else I have tried running or install. 

That's not good news -- but this isn't a Windows forum, so, let's not go into lots of details about XP SP2 not working.  But, given your previous error messages, it still seems like a failing drive.

> 
Ubuntu will not intall and are not willing to run the partition editor. It seams to run OK as live CD.

Running OK as a LiveCD doesn't really say anything about the health of the hard drive.  Suggest you boot into Windows XP and run chkdsk a few times. If it keeps getting errors time after time, you have a failing drive.  If it only gets errors the first time, and subsequent runs are error free, it only needed chkdsk run to clean up the filesystem problems.  

Ubuntu should then install.

---

### Post by 2blue on 2009-02-13
I know it is a bit annoying with all the windows talk on a Ubuntu forum. However it seams the easiest to start with fixing and installing the windows system and then do the partition for Ubuntu. Even thogh I spend most of my time exploring Ubuntu and linux these days I very much need all the functions in in Windows Office.

---

### Post by 2blue on 2009-02-13
I have rund chkdsk several time. I get "warning!, F-parameters not set!". System runs the command it proteced modus. 16 KB of the harddisk has damadged parts. 

I then typed in "chkdsk/F, but it could not run this command, something was preventing the system of doing that.

---

