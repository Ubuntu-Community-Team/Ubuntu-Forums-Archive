---
title: "Home Network Ubuntu to Ubuntu - Help!!!"
date: 2005-11-01
forum: Networking &amp; Wireless
---

### Post by KrazyPenguin on 2005-11-01
I am a nOOb to networking so please help!!!!

I have 2 computers running Ubuntu both sharing a D-Link connection to the internet.

I was wondering if there are any guides to setting up a network for Ubuntu to Ubuntu (Breezy to Breezy)????

It seems that I have to install Samba. But I have heard that only one machine needs the Samba.  Is this Correct???

Thanks.

---

### Post by RayH on 2005-11-01
Install samba on whichever computer(s) that you want to share a folder from.  Install smbfs on whichever computer(s) that you want to connect to a share.

Searching for "samba" will get you a couple of how-to docs on how to specifically set it up.  Once you do that you'll be able to browse to the samba server and the share that you setup with it.  If you want to automatically mount the drive/share on the client PC, search for "smbfs" and "fstab" and that should teach you what you need to know.

---

### Post by KrazyPenguin on 2005-11-01
[QUOTE=RayH]Install samba on whichever computer(s) that you want to share a folder from.  Install smbfs on whichever computer(s) that you want to connect to a share.

Searching for "samba" will get you a couple of how-to docs on how to specifically set it up.  Once you do that you'll be able to browse to the samba server and the share that you setup with it.  If you want to automatically mount the drive/share on the client PC, search for "smbfs" and "fstab" and that should teach you what you need to know.[/QUOTE]


OK I will try that.   I am finding it tough to find information about this on the internet written in plain english.  One day, If i figure this out, I will write my own how-to.

Thanks for the starting point tips.  ;-)

I will let you know how it goes.

---

### Post by wylfing on 2005-11-01
I want to tidy this up. KrazyPenguin went off and started another thread here:
[http://www.ubuntuforums.org/showthread.php?t=85144](http://www.ubuntuforums.org/showthread.php?t=85144)

Now, the solution to this problem is to use NFS, as he (apparently?) learned in the conclusion of the other thread. Samba is an appropriate sharing solution when there are Windows computers in the network. If you don't have to support Windows computers, don't use Samba. Use NFS. (Printer sharing is handled automagically by CUPS.)

All you need to do to get started sharing things with NFS is to right-click on a folder in Nautilus and choose Share folder. Select NFS from the Share with drop-down list, specify who can connect (for most home network users choosing the "Hosts in the eth0 network" works fine), and you're off and running.

Long story short: Samba is finicky and breakable. NFS is nice.

---

### Post by Biased turkey on 2005-11-02
If you only have 2 computers ( that's my situation too ) why not just use ssh, it's so simple and is installed by default with ubuntu.
On my ( minimum ) home network I started using ssh,  ( with cups for sharing the printer ),  then last week I installed samba just to see how samba works and because the client dualboot ( Ubuntu and windows ).
The server must have samba installed and the client must have smbfs installed ( as mentioned by RayH.
If both rigs run Linux only, then wylfing is right about going the NFS way.
Ah the beauty of Linux: NFS ? Samba ? ssh ? the choice is up to you.

---

### Post by KrazyPenguin on 2005-11-04
I have never heard of ssh??? Is it easier to use then NFS??
Is it more secure???

I don't even know where to start LOL.

:confused: 

I tried the NFS but can't view anything on the other computer.
Do I need to mount something, or do you think my Firestarter settings are wrong??

---

### Post by KLineD on 2005-11-04
SSH is a secure shell to log into your computer remotely. I for example, use it to log into my ubuntu machine from work (windows) and get the shell. You can also use it to transfer files using scp. If you have it installed, try it out: ssh ipaddress

However I do recommend to use NFS to network two ubuntus.

---

