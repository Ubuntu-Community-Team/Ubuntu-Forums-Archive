---
title: "Samba Password request"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by VoyeurOne on 2007-10-15
I finally have my networking working somewhat, I mounted my windows shares in a folder called laptop in my home folder and made a password file in my Samba directory with my username and password for the XP laptop, it's not what I wanted but if the laptop is on when I restart Feisty I can at least use the XP share.  From XP to Feisty it works as it should I can scan the network and access Samba shares at will.

My problem is that I noticed my Samba shares no longer require a password.  I used to get prompted input my User Name and password on connect from the XP Laptop but it stopped asking all of a sudden, it didn't concern me as my widows and Feisty user name and password are the same I thought I was getting instant access because my username and pass were sent along with the packets from the windows machine.

 Last night I booted the laptop with a linux live CD and was able to browse all samba shares without getting prompted for a password.  Does anyone have an Idea what I might have changed to allow this to happen?   I did not change SMB.conf when I set up the network but I did put a smbpasswrd file in the Samba folder that is read by my fstab file when trying to mount the windows shares.   I think I might have overwritten an existing Samba password file when I put mine in the directory and now that Samba sees no password file it thinks that it's ok for everyone to connect, but other than that I have no idea what I messed up.

---

