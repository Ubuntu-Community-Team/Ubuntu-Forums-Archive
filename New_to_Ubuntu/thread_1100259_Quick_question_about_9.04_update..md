---
title: "Quick question about 9.04 update."
date: 2009-03-19
forum: New to Ubuntu
---

### Post by djk21108 on 2009-03-19
Hi, I'm just curious about what the upgrade process will be to 9.04 from 8.10.  This will be my first linux upgrade and I'm wondering if I'll have to download the whole big live cd again, or what.

---

### Post by theozzlives on 2009-03-19
You can download the alternate CD and if you put it in with Ubuntu running, it should give you the option to upgrade.

---

### Post by leonardo_neo on 2009-03-19
> **theozzlives said:**
> You can download the alternate CD and if you put it in with Ubuntu running, it should give you the option to upgrade.

I don't think I should start a new thread for this question, I just want to ask, in case of upgrade like this, will the existing ext3 files be converted to ext4?

---

### Post by Paqman on 2009-03-19
> **leonardo_neo said:**
> I don't think I should start a new thread for this question, I just want to ask, in case of upgrade like this, will the existing ext3 files be converted to ext4?

If you do an in-place upgrade (either using a CD as a repo or through the internet) then no, you won't get the option to switch to EXT4. I believe there is a way to convert an existing EXT3 partition to EXT4 without formatting it, but it's not part of the Ubuntu upgrade process.

To get EXT4 you'll have to reinstall from scratch and choose manual partitioning. It'll let you select EXT4 for your partitions instead of the default EXT3.

But to go back to your question djk21108: When Jaunty is released you'll get a notification from the update manager that you can upgrade. You can do that any time you like, and it's not compulsory. It's also quite a big download, and the servers get pretty swamped around release time, so it could be painfully slow. If you decide to upgrade it's best to wait a few days after release.

If you really want to have Jaunty as soon as you can, best thing to do is torrent the LiveCD and reinstall from scratch.

---

### Post by trooperchix on 2009-03-20
Can I do the upgrade with a live or alternate CD from boot?  I absolutely have no access to my keyboard or PF keys, so I can't even get into the terminal (switching session types don't work either).  I don't know how to access that hard drive to back up my stuff, so if yu can add that info as well, that would be peachy.

---

### Post by thiebaude on 2009-03-20
or you can upgrade from 8.10 using update-manager -d

---

### Post by trooperchix on 2009-03-20
> **thiebaude said:**
> or you can upgrade from 8.10 using update-manager -d
Alright, how do I do this.  Keep in mind my keyboard doesn't work at all.  Maybe move the HD from one system to another and see if it will boot on that one?  I think I'll give that a try...

---

### Post by trooperchix on 2009-03-20
*bump*

---

### Post by mlentink on 2009-03-20
Why can't you use a keyboard? Is this by any chance a headless server?

---

### Post by trooperchix on 2009-03-20
There is some issue on Dell computers that affect the keyboard.  Dell has sat on their thumbs with this because it is thought this is a linux kernel issue.  I need to access terminal and type so  I can get my kernel updated.  that is supposed to fix the issue.  This is a simple home laptop.

---

### Post by malibusurfer2 on 2009-03-22
Have you tried booting from an Ubuntu CD to see if your keyboard works? If it does, then the safest procedure would be to connect an external USB HD, backup all your data and bookmarks and email, etc, and try to do an upgrade from the CD. Good luck.

---

### Post by trooperchix on 2009-03-23
> **malibusurfer2 said:**
> Have you tried booting from an Ubuntu CD to see if your keyboard works? If it does, then the safest procedure would be to connect an external USB HD, backup all your data and bookmarks and email, etc, and try to do an upgrade from the CD. Good luck.

I don't have access even with the Live CD (weird, don't know why) but I have figured out I can access the hard drive through my network on another Ubuntu laptop.  I'm so peeved, I have so much music and family pictures on that bugger....

---

### Post by hyper_ch on 2009-03-23
I wouldn't use EXT4 yet.

---

### Post by GepettoBR on 2009-03-23
> **hyper_ch said:**
> I wouldn't use EXT4 yet.

I'm running Arch from an EXT4 volume and it works fine. But it still isn't completely stable, so I'd advise against using EXT4 on the partition where you store your personal files.

---

