---
title: "Can't see network, but can see IP's"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by blenderfish on 2007-03-12
So I have a home network consisting of a Ubuntu laptop, a Windows XP laptop, and a Ubuntu Desktop, all connected through a Netgear wireless router.  The desktop is connected by a physical line, while the others are wireless.  I am using the desktop strictly for file storage, and I am moving files from the windows laptop (my old PC) to the desktop for this purpose.  My router is set to assign static IPs to the machines.

So I followed this [tutorial]("http://www.ubuntuforums.org/showthread.php?p=2284928#post2284928") for setting up Samba on the two Ubuntu boxes.  Now, I have all three turned on, and the windows machine sees both Ubuntu machines in the Windows Network, and I can transfer files to the share on the Desktop no problem.  

The problem is that my ubuntu machines don't see things so easily.  Under network servers -> Windows Network, the laptop sees my workgroup name, but when I double click on it, I get the message: "The folder contents could not be displayed.".    Meanwhile, if I do a Connect to server and specify the IP address of the desktop, it works and I can see the files.  The desktop can see the workgroup, and the computers in the workgroup, but when i click on the individual computer, I get the same error message. 

Any ideas?  The followup question is, how do I mount a network drive permamently?

---

### Post by [S|G] on 2007-03-12
> **blenderfish said:**
> (...) The followup question is, how do I mount a network drive permamently?
You can place a line like this on your fstab:

```
\\host\directory          /path/to/mount  smbfs users,rw,username=loginToShare,password=passwordToShare   0       0
```

---

### Post by blenderfish on 2007-03-12
Thanks S|G.  I'm still having this base issue though.  I can totally browse and manipulate files when addressing the computers by IP, but I can't browse freely through the Windows Network like I would like to.  I'm even having a similar issue on the XP machine now after I added a second share to the Desktop machine.  

Anybody?

---

