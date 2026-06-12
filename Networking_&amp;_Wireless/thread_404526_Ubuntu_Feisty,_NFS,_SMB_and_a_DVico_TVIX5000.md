---
title: "Ubuntu Feisty, NFS, SMB and a DVico TVIX5000"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by igadgetman on 2007-04-08
At the moment I'm running FreeNAS from an USB stick so I can share my mediafiles from this machine I call my Fileserver. The plan is to add a Addonics Port Multiplier to it with 5 SATA2 500Gb drives connected. Googling learned me that FreeNAS is NOT supporting a portmultiplier and Ubuntu according to search results is.

I have 3 IDE hd's in this Pentium4 (531) connected to an Asus P5VD2-MX board.  
1x 40Gb and 2x120Gb at the moment.
I installed Feisty beta on the 40Gb drive and the 2 120Gb drives are UFS formatted just in case I need to return to FreeNAS again.
In my network are also 2 mediaplayers, 1 Freecom MG35kit and 1 DVICO TVIX-M5000U.
The latter is capable to connect through NFS.

What I want is being able to connect  the mediaplayers to the Ubuntu machine. My Windows XP system needs also to be able to put files to the Ubuntu system.

I tried setting up NFS and SMB, but my TVIX is not seeing the NFS shared folder.
With SMB, my windows system wants passwords which are not accepted. I know i'm missing some critical commands.

Anyone out there with a TVIX 5000 and an Ubuntu system who can help me to get it to work?

---

### Post by indyr on 2008-03-12
Good morning,
I have a configuration quite similar to yours. Some of my computers are under Windows and others are under Ubuntu. I think some precisions are required here :
- Your Tvix is connected via wifi or cable? If it is wifi, check that your "AP isolation" option is unchecked
- Does your Windows session require password to be accessed? I think it is necessary to use authetication
- Have you checked the M5000 doc? Some operations are needed to allow TVIX to connect to Samba disks

---

