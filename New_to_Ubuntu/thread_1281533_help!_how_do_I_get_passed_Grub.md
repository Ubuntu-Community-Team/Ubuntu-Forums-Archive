---
title: "help! how do I get passed Grub?"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by djamieson on 2009-10-03
Hi, I have no knowledge of ubuntu and managed to do some damage to my Dell Mini 9.

Basically I forgot my user password. So after checking forums etc. discovered that I needed to get into the boot options. However, I re-set what I think is the system password and HDD password in the 'security' section of the Utility Set-up. I now think this is probably a different password from the user password.

Anyway, now when I try and use the computer I get stuck with the following:

Grub>

This is probably straight forward but with virtually no knowledge I'm totally in the dark. All I want to do is get back to having a normal OS. Any help would be so much appreciated.

---

### Post by Paddy Landau on 2009-10-03
See the [Community Help Grub HowTo - Command line]("https://help.ubuntu.com/community/GrubHowto#Command%20line").

In short:

[LIST=1]
[*]Boot with your live CD.
[*]Open a terminal window.
[*]Type *sudo grub*
[*]Type *find /boot/grub/stage1* and you'll get a response like *(hd0,1)*. Note what it says.
[*]Type *root (hd0,1)* but use what you got in step 4.
[*]Type *setup (hd0,1)* -- again, use what you got in step 4.
[*]Type *quit*
[/LIST]
Reboot to see if it worked.

---

### Post by steveneddy on 2009-10-03
> how do I get [COLOR=Red]**passed**[/COLOR] Grub?

[COLOR=Green]**past**[/COLOR]

---

### Post by djamieson on 2009-10-03
> **Paddy Landau said:**
> See the [Community Help Grub HowTo - Command line]("https://help.ubuntu.com/community/GrubHowto#Command%20line").

In short:

[LIST=1]
[*]Boot with your live CD.
[*]Open a terminal window.
[*]Type *sudo grub*
[*]Type *find /boot/grub/stage1* and you'll get a response like *(hd0,1)*. Note what it says.
[*]Type *root (hd0,1)* but use what you got in step 4.
[*]Type *setup (hd0,1)* -- again, use what you got in step 4.
[*]Type *quit*
[/LIST]
Reboot to see if it worked.
Hi thanks Paddy.

My Dell Mini 9 doesn't have a drive for the CD. Ubuntu was already installed. I do have the CD however. Should I transfer onto an external drive and use it via USB? If so, does the process you gave me change at all?

---

### Post by Paddy Landau on 2009-10-03
> **djamieson said:**
> Should I transfer onto an external drive and use it via USB? If so, does the process you gave me change at all?
Yes, do that. The process should be as I've described.

---

### Post by djamieson on 2009-10-03
sorry about this, getting 'Operating System not found' when trying to boot with external drive. Any ideas?

---

### Post by Paddy Landau on 2009-10-03
> **djamieson said:**
> 'Operating System not found'
Sorry, I'm no expert in this. Have you ensured that you made your external drive bootable?

There are only two ways that I know of.

[LIST=1]
[*]Download [Ubuntu Netbook Remix]("http://www.ubuntu.com/getubuntu/download-netbook") and [follow the instructions]("https://help.ubuntu.com/community/Installation/FromImgFiles").
[*]Install unetbootin (only with 8.10 or higher) and use it to copy the .iso image to the USB drive.
[/LIST]
Oh, and you can also open GParted (System > Adminstration > Partition Editor), right-click the partition for the USB drive, Mange Flags, and ensure that "boot" is checked.

Perhaps someone else on the forum can help further.

---

### Post by louieb on 2009-10-03
> **djamieson said:**
> 
My Dell Mini 9 doesn't have a drive for the CD...I get stuck with the following:

Grub>

you can pickup Paddys sugestion once you get the **grub>** prompt  (thats what his 1st three steps did).
> **Paddy Landau said:**
> 
[LIST=1]
[*]Type *find /boot/grub/stage1* and you'll get a response like *(hd0,1)*. Note what it says.
[*]Type *root (hd0,1)* but use what you got in step 4.
[*]Type *setup (hd0,1)* -- again, use what you got in step 4.
[*]Type *quit*
[/LIST]
Reboot to see if it worked.

---

