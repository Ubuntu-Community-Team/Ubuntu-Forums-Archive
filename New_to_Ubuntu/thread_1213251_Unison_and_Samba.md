---
title: "Unison and Samba?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by zcacogp on 2009-07-14
Chaps, 

I have a desktop computer. 

I have a laptop computer. 

I have (with MUCH difficulty) managed to make the desktop drives accessible from the laptop computer (see here: [http://ubuntuforums.org/showthread.php?t=1182827](http://ubuntuforums.org/showthread.php?t=1182827)) using Samba. In short, I have a drive on the desktop called Ianthe, and a drive on the Laptop called Ieuan. (I also have a drive on the desktop called Helena, and a drive on the laptop called Horatio). 

I have downloaded and installed Unison on the laptop, and am trying to use it to keep Ianthe and Ieuan in sync. There are updated files and folders on both sides of the sync. 

Everything says it is easy, but I cannot make Unison read the Desktop drives from the laptop, using Samba. The "set up profile" in Unison allows me to specify a "Local", "SSH", "RSH" or "Socket", but not a Samba connection. I can see the drive on the desktop computer from the laptop computer, where it appears as smb://ogp-desktop/ianthe/, but I can't make Unison talk to it. 

Any suggestions? 


Oli.

---

### Post by zcacogp on 2009-07-16
OK, sorted this one out. 

Had to use SSH - it seems that Unison won't work with Samba. 


Oli.

---

