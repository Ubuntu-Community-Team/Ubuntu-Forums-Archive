---
title: "how do i set up a home network?"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by Mzwo on 2008-08-13
hi all,

i'm running hardy on my laptop, hardy and xp on my pc and xp only on a third laptop and i want to make them all talk to each other. how would i go about doing this? main objective: access folders and files. 

pc's connected to router via ethernet, laptops both via wifi.

please try to avoid jargon and other linux-speak when replying, i'm a complete greenhorn.

many thanks,   
Mzwo

---

### Post by bab1 on 2008-08-13
The simple answer is -- use Samba to talk among the various hosts (PC or Laptops).  As I have only set it up at it's lowest level (editing the config files), I won't be of any help with the GUI setup.

---

### Post by rbc on 2008-08-13
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

and 

[http://www.wonderhowto.com/how-to/video/how-to-share-windows-files-with-ubuntu-linux-using-samba-137549/](http://www.wonderhowto.com/how-to/video/how-to-share-windows-files-with-ubuntu-linux-using-samba-137549/)

The second one is a video that will walk you right through it

---

### Post by rbc on 2008-08-13
Also, check synaptic for system-config-samba. I have not used it, but it supposed to be a GUI way of setting up shares

---

### Post by Mzwo on 2008-08-13
thanks for the quick replies.

will samba also serve to connect ubuntu to ubuntu?

---

### Post by rbc on 2008-08-13
It will indeed. There are supposed to be better way of sharing Linux to Linux, but I have never used those methods because I also have a Windows in the mix

---

### Post by bab1 on 2008-08-13
NFS is the linux to linux method.  But as new user, I don't reccomend you try it.

---

### Post by Mzwo on 2008-08-13
ta very much. 

Mzwo

---

### Post by Mzwo on 2008-08-21
sorry to bother you again guys - none of the above worked. i'm running hardy and some instructions seem to refer to earlier ubuntus, things seem to have changed ...

any chance that somebody could walk me through how to share a drive on my pc via a home network? 

cheers,

Mzwo

---

### Post by Iowan on 2008-08-21
A couple more How-To's to check:
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

