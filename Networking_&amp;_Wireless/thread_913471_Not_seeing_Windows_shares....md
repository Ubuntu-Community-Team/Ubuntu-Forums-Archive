---
title: "Not seeing Windows shares..."
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by elishock2420 on 2008-09-07
Running 8.04, having an issue when trying to browse smb shares.  When browsing using nautilus to smb://servername I see nothing.  However I can access the shares if I use smb://servername/sharename  and then can browse through all subfolders with now issues.  It's a real annoyance, any help will be appreciated.  Thanks!

---

### Post by gregphil on 2008-09-07
I think it is an ubuntu bug the the nautilus network file browser:

[http://ubuntuforums.org/showthread.php?t=909453](http://ubuntuforums.org/showthread.php?t=909453)  
(go all the way to the end of the 2nd forum page for a "work-around")

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520)

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/72341](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/72341)

---

### Post by bab1 on 2008-09-07
Check to see if you have installed the the Samba client (smbfs).  If not install from the terminal:```
sudo apt-get install smbfs
```

---

### Post by elishock2420 on 2008-09-08
I have this package installed already.  Anything else you can think of?

---

### Post by gregphil on 2008-09-08
Appears to be a long standing bug (still in Intrepid Alpha 5)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

---

### Post by elishock2420 on 2008-09-09
This is a real bummer....
Thanks to all of those that replied.

---

### Post by gregphil on 2008-09-09
There are work-arounds....

You can simply enter the FULL text share name in the applicaion you are trying to browse with, and then press enter.

For example in the nautilus network file browser, after you see the list of computers, click on one of the Windows computer icons (this leads to a blank browse screen). Then change the input box to text (click on the pencil in the upper left) and append the share name to the network path. Press enter. If you entered a valid share name the nautilus file browser will now prompt you for the username & password and then connect and allow browsing of that share.

You can find the name of the available shares by using the command line "smbclinet -L COMPUTERNAME" That will prompt you for the password (assumes your logged on username) and then show the available shares on COMPUTERNAME.  If you look on the Windows boxes you can figure out the share names form there (I know this is not real "browsing", but I did use the phrase "work-around")

Good Luck.

---

