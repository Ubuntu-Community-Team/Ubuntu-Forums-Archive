---
title: "Default network password?"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by mikeaguilar1 on 2007-02-22
When i use my laptop (windows) 

and go to MSHome network and i try to get in to my desktop (unbuntu) it ask for a user and password but i never set a password for it.

What is it?

---

### Post by gradedcheese on 2007-02-22
Hi.  Please read this:  [http://andrey.thedotcommune.com/samba.html](http://andrey.thedotcommune.com/samba.html) -- essentially, you need to set a password and my page will explain how.

---

### Post by mikeaguilar1 on 2007-04-20
I looked over that and am sooooo confused

Can someone break it down for me step by step please.

---

### Post by salthog on 2007-05-08
All you need to set up is a SAMBA password.

In the Terminal Window enter

*sudo smbpasswd -a youruser*

This will set up a password in the SAMBA password database for "youruser". You will have already setup a Linux user when you installed Ubuntu - use the same one. The SAMBA password does not have to be the same as your user password (and I would not recommend it as it will be stored on your windows PC).

Once you have connectivity established, you can look at some of the other SAMBA configuration items from the earlier post.

---

### Post by salthog on 2007-05-09
Oh, I forgot to say that you would have to restart SAMBA after setting the password:

*sudo /etc/init.d/samba restart*

---

### Post by gutsy galt on 2008-04-16
Hi

I followed the steps outlined above for setting a SAMBA password,restarting Samba, then accessing a shared folder through my Windows XP laptop.  After entering the correct username and password, I still get an error message:  "The folder you entered does not appear to be valid.  Please choose another."

The folder is named "Share" and is located in the home folder.  I've set the folder to be a shared folder through Windows networks (SMB).  Ubuntu tells me the folder path is /home/myusername/Share.

The address I enter to access it from windows is 
\\mycomputersname\home\myusername\Share

What am I doing wrong?

---

### Post by Iowan on 2008-04-16
See if this [HOW-TO]("http://ubuntuforums.org/showthread.php?t=202605") helps.

---

### Post by dfreer on 2008-05-08
> **gutsy galt said:**
> Hi

I followed the steps outlined above for setting a SAMBA password,restarting Samba, then accessing a shared folder through my Windows XP laptop.  After entering the correct username and password, I still get an error message:  "The folder you entered does not appear to be valid.  Please choose another."

The folder is named "Share" and is located in the home folder.  I've set the folder to be a shared folder through Windows networks (SMB).  Ubuntu tells me the folder path is /home/myusername/Share.

The address I enter to access it from windows is 
\\mycomputersname\home\myusername\Share

What am I doing wrong?

Not sure if this is the only problem you are having, but at least the share would not be at \\mycomputersname\home\myusername\Share, it should be at \\mycomputersname\Share.

---

