---
title: "Upgrading to Karmic"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by ehderube on 2010-03-01
Hi,

I have been using ubuntu for over 2 years and like it!  I enjoy how most things can be customized but I upgraded to Karmic (9.10 kernel: 2.6.31-19-generic) and the boot time isn't great.  While doing some research on the topic I came across some other things that haven't been updated with each new release.  I typically just use the update manager and don't bother with reading about the new features with the releases.  So I found out that there is a new drive format (ext4) and grub has been upgraded to 2.0 (I'm using 0.97!).  So my question is it better to do a fresh install or is just using the update manager OK?

---

### Post by NightwishFan on 2010-03-01
You can upgrade the disk format manually to ext4, but I doubt you will much notice any difference. If you want to try it regardless, I would advise backing up your files and settings and doing a fresh install.

Here is some more info about ext4 and using it without reinstalling:
[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

---

### Post by ehderube on 2010-03-01
Thanks for the reply,

So, is there any need to upgrade the filesystem or bootloader?  If not I will just keep what I have.

---

### Post by NightwishFan on 2010-03-01
No there is no need.

---

### Post by lavinog on 2010-03-01
What are the system specs?
Some systems seemed to have slower boots, while others seemed to have quicker.
ureadahead is a major change in karmic.
I have experienced some bugs with it, and have uninstalled it.
Some users have pointed out that grub2 has slowed down their boot also.

---

### Post by k3lt01 on 2010-03-02
My preference is to do a clean install so that I get the new features when they are available. If you stay with old features such as Grub Legacy (Grub 0.97 etc) then you will eventually come to a point that you will no longer be able to update properly as the old features are no longer supported.

Also with regards to Lavinog's comment. Ureadahead (which come through as an update in Karmic) proved to be a major bottleneck to my laptop so much so that I do not allow it to install (as an update) or remove it (if it installs as OEM) on any system I work with. I do however know of systems it has not been a problem on. The point of this is to impress upon you, and others, that it is always prudent to be a wise consumer. In other words keep asking questions and make up your mind based on real world examples.

---

