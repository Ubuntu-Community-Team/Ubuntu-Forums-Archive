---
title: "mount smbfs - linux to linux"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by HereInOz on 2007-03-17
Hi all,

I found some techniques on this, both in this forum and others, but even so, things aren't working.

I have 2 Linux machines, one with a Samba share on it.  I want to be able to mount that Samba share in a directory on my other Linux machine, preferably on bootup.  Samba is installed on both machines.

I found a webpage with instructions on how to do this, and from one of these webpages, I entered the command:

sudo mount -t smbfs //server/share /home/myusername/mount -o username=myusername,password=mypassword   
(of course, using the correct directory names and samba username and password), and I received the following message:

mount: wrong fs type, bad option, bad superblock on //server/share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The error log from dmesg is:

smbfs: mount_data version 1919251317 is not supported.

Has anyone got any clues about what I am missing out on?  Once I sort this out, I can blunder on and make the mount permanent, but until I can sort this out, it is not possible.

Hope you can help.

Alan

---

### Post by cosborn72 on 2007-03-17
This may be a dumb question, but have you gone into Synaptic/Adept and installed the require smb support files?

I believe the package you need is called smbfs, but it may be called smbclient or just smb.  I would do a search for smb and install any of those three that come up.

---

### Post by HereInOz on 2007-03-17
Yep, that was it.  I had all the samba stuff installed apart from smbfs.  When that was installed, all went well.  

Thank you very much for the assistance.

---

### Post by thierrybo on 2007-03-17
I experienced a similar problem. I have a samba share on breezy and mount  this share successfully from another breezy. When I tried from a Dapper (not tested fro Dapper to Dapper), my desktop freezes on the Dapper side. I can mount but this happens as soon I try to access the share.

---

### Post by HereInOz on 2007-03-17
I can't help you there - as you can see from my post, this is not my strong area of Ubuntu.  

All I can think about is perhaps there is an application or library that is installed on your Breezy machines which is not installed on the Dapper machine, but I would have no idea what that may be.

Maybe have a look on the Breezy machines in Synaptic and see what is installed using a search of "samba" and / or "smb" and check it against your Dapper installation.

Hopefully someone with more knowledge than I in this area will assist.

---

### Post by dbott67 on 2007-03-17
You can try this thread:

[http://www.ubuntuforums.org/showthread.php?p=1637029#post1637029](http://www.ubuntuforums.org/showthread.php?p=1637029#post1637029)

-Dave

---

