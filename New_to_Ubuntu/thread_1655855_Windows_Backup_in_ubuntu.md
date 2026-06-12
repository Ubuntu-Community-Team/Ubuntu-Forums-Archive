---
title: "Windows Backup in ubuntu"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by zammil on 2010-12-30
Hi Friends,  I want to ask about windows backup in ubuntu.i have installed ubuntu and windows in two separate disks. so I'm able to see all system and boot  folders in windows using ubuntu  but ubuntu system files is not visible in windows.since windows is vulnerable to crashes and malicious threats i have to format windows often which is harmful to hard disk and time consuming also .so I'm thinking about backing up windows system files n ubuntu.I'm planning to copy windows folder including boot files  in  the c: drive on to the ubuntu system folder where it cannot be modified or is invisible to the windows operating system.so whenever  my windows os gets affected i just have to log into ubuntu and replace the original windows folder with the one saved in ubuntu system folder so it is like a newly formatted windows os . This is just my imagination and i don't know if it will work or not that's why  I'm asking you guys  the professionals.plz tell me if it's possible or not or do i have to  save the entire c: drive in ubuntu    Thanks in Advance

---

### Post by cipherboy_loc on 2010-12-30
> **zammil said:**
> i have to format windows often which is harmful to hard disk and time consuming also 

Formatting is not harmful to the hard disk. 

> **zammil said:**
> since windows is vulnerable to crashes and malicious threats
Why not get an Anti-Virus program? 

> **zammil said:**
> so whenever  my windows os gets affected i just have to log into ubuntu  and replace the original windows folder with the one saved in ubuntu  system folder so it is like a newly formatted windows os
What about updates to you computer? You will have to "backup" your C:\ drive often to get all the update (Firefox, and a bunch of system updates). Unless you never update your Windows system, which would be another issue.


If I understand you correctly, I am doing something similar, where I compress the entire C:\ drive from Ubuntu and save it on an External Hard Drive. 


So, if you get EVERYTHING, you should be fine.


Sorry if that seamed like a flame, I can remove most of it if you want,
Cipherboy

---

### Post by serdar255 on 2010-12-30
im sorry if im wasting anyones time but how do i make a post on the forum

---

### Post by blind2314 on 2010-12-30
Go to the section of the forum you want to post in, and click the "new thread" button, on the top or bottom left of the page, either one.

---

### Post by mike555 on 2010-12-30
There are a number of backup /cloning programs for Windows , like xxclone , clonezilla,etc.

---

### Post by theozzlives on 2010-12-30
1. mount your windows partition.
2. Lets say it mounts in /media/disk:
```
sudo tar cvpzf windows.tgz /media/disk
```
3. To restore do:
```
sudo tar xvpfz windows.tgz -C /media/disk
```

---

### Post by zammil on 2010-12-30
> **cipherboy_loc said:**
> Formatting is not harmful to the hard disk. 

    I'm not  sure about harmful or not but it is time consuming 


> **cipherboy_loc said:**
> Why not get an Anti-Virus program?

all anti virus programs cannot guarantee 100% security.the system is always prone to threats in case of windows.


> **cipherboy_loc said:**
> What about updates to you computer? You will have to "backup" your C:\ drive often to get all the update (Firefox, and a bunch of system updates). Unless you never update your Windows system, which would be another issue.If I understand you correctly, I am doing something similar, where I compress the entire C:\ drive from Ubuntu and save it on an External Hard Drive. Cipherboy

I don't care about updates.i will specify it clearly.i will format my current windows os and then copy the  new "windows" folder  to ubuntu system folder.if anything go wrong in my windows os does restoring the windows folder in ubuntu make my windows as it where  when it was formatted or do i have to copy the entire c: drive.will it work??or do i have to use windows cloning software???

---

### Post by zammil on 2010-12-31
> **theozzlives said:**
> 1. mount your windows partition.
2. Lets say it mounts in /media/disk:
```
sudo tar cvpzf windows.tgz /media/disk
```3. To restore do:
```
sudo tar xvpfz windows.tgz -C /media/disk
```

can u specify what it does i mean  where does it mount the windows partition.to the ubuntu root folder or any other local disk.i only want the system folders to be restored 

is this the easiest method compared to cloning  softwares

---

### Post by theozzlives on 2010-12-31
/media is a folder off the root folder /media/disk is just an example. Your Windows Partition may mount under a different name than "disk". The easiest way to mount is to go to places and click on your Windows filesystem, then go to /media and find what it calls the mountpoint of your Windows.

Concerning antivirus, Microsoft Security Essentials seems to work well with GENUINE Windows and it's free.

---

### Post by Mark Phelps on 2011-01-01
> **zammil said:**
> ...I only want the system folders to be restored

What you appear to be asking for is a way to save off only the "system" components of MS Windows -- and restore only those later.

This simply is NOT possible -- regardless of what anyone here may tell you otherwise.

Sure, you could try to identify the individual folders (of which there are hundreds!), but the major hangup is going to be the registry -- a collection of proprietary format files (known as "hives") that contain tens of THOUSANDS of entries -- only SOME of which are related to "system" components.  You're NOT going to be able to save off only the "system" entries.

You would do better using an MS Windows app (one of the best Free ones is known as Macrium Reflect) to image off the MS Windows OS partition.  That way, you could restore that later if needed -- but it will restore the entire partition.

---

