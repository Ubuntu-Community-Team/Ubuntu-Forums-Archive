---
title: "Cannot See Window Machines on Network"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by juniah on 2007-12-08
My roommates have those nifty shared folders from Windows and want to share with me.  How quaint.  However I can't see their machines.  I've been trying to follow some of the solves on here, but I'm getting lost.  I'm running Ubuntu 7.10 if that helps at all....

---

### Post by jimrz on 2007-12-08
assuming that you have already installed samba, check and make sure that the name of your "workgroup" in /etc/samba/smb.conf exactly matches the workgroup name on your roommates win boxes.

---

### Post by juniah on 2007-12-08
how do I configure samba....

wiki link?

---

### Post by Jumpmasterrt on 2007-12-08
You can do it one of two ways, you can use SWAT (Samba Web Admin Tool) or in the terminal.
```
 sudo gedit /etc/samba/smb.conf 
```

---

### Post by jetsam on 2007-12-08
It's possible you have an obscure bug that some people have reported with the latest Samba security update.  Do you have a Gutsy live cd?  If you boot it and can browse the network from the live cd, then you probably have the bug.  

In theory, windows network browsing should work from Places-->Network without any configuration in Gutsy.  Even mixed workgroup names should just show up as different workgroups to browse.

One possible solution, if you do have the bug, is in my post, the third in this thread:  [http://ubuntuforums.org/showthread.php?t=626861]("http://ubuntuforums.org/showthread.php?t=626861")

---

### Post by linuxaddict on 2007-12-08
I had this same problem. When you're looking at your network through Places => Network, try putting in smb://Windows box IP. This worked, and then I just bookmarked it and saved it with a name for each computer.

---

### Post by bwanaaa on 2007-12-15
i have the same problem:
browsing the network shows my workgroup
double clicking on the workgroup gives the following error dialog:

The folder contents could not be displayed

Sorry, couldn't display all the contents of "Windows Network: workgroup".




But i can browse to all of the samba shares in the network by simply typing in the ip address. Why is this?

---

### Post by tuproxy on 2007-12-16
I had the same problem with 6.10 and couldn't figure it out.  I had Samba set up correctly and was able to share/map from my linux box to my XP box.  

I have never had shares work so well as with Linux / Samba.  It is lightning fast when searching the linux box from an XP machine.

---

### Post by Tekno_Cowboy on 2007-12-16
I'm having a similar problem where I can access outside internet and see the workgroups on the network, but cannot access the workgroups. my samba conf file matches. I get an error about timining out, but that's about it. I did not try the IP address trick, but it wouldn't be practical, as the IP numbers change frequently. I had no problems on my laptop running Feisty, now running gutsy and it refuses to work.

---

### Post by jetsam on 2007-12-22
A person in this thread-- [http://ubuntuforums.org/showthread.php?t=643256]("http://ubuntuforums.org/showthread.php?t=643256") -- was able to fix their browsing problems by disabling roaming mode in System-->Administration-->Network and setting their network connection to use DHCP.  It's probably worth a try; see post # 7 of that thread.

---

