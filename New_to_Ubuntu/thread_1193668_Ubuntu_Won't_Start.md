---
title: "Ubuntu Won't Start"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by azrulyahya77 on 2009-06-21
Hi,

I've installed Ubuntu 9.04 in my computer. The thing is that, i cannot start Ubuntu without first inserting the Live CD and chose 'Boot From First HDD'.

I'll appreciated if anybody can help me to solve this problem. I'm new in Linux and i do not know a thing about it. :)

Thanks in advance.

(Sorry, english is not my first language)

---

### Post by halitech on 2009-06-21
when you installed, where did you install GRUB?

---

### Post by Sealbhach on 2009-06-21
Looks like Grub didn't install properly.

Try these steps here (1 to 5):

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

.

---

### Post by RedSingularity on 2009-06-21
What is the problem you are experiencing?  I mean is there a message or some text that pops up?

---

### Post by LewRockwell on 2009-06-21
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by azrulyahya77 on 2009-06-22
Hi,

Thank you for the reply and solution that you all have given to me. I have tried to all of the suggestion, but to no avail. Maybe i'm forgot to tell you that i was using 2 HDD;

i)  80GB Maxtor - previously installed the Ubuntu in it ( deleted it using KillDisk )
ii) 160GB Seagate - installed Ubuntu- previously Win XP Home ( deleted it using KillDisk )

After i've deleted both the HDD using KillDisk, i still see the grub loads but with an error msg. I ignored the error msg and continue to install the Ubuntu to the 160GB Seagate HDD.
The installation went smooth but after i restarted my computer, i cannot get Ubuntu to start unless i'm using the LiveCD by choosing 'Boot From The First HDD'.

And then i decided to unplug my 80GB Maxtor HDD, and to my surprise the Ubuntu can boot !
I still cannot understand why, but nonetheless thank you very much for all the suggestion.

I now can start using my Ubuntu without problem. Thanks again :)

---

### Post by tarps87 on 2009-06-22
It sounds like you are using the drive with Ubuntu on as a slave drive, this is either a bios setting or a jumper on the back of the hard drive. From you post I am assuming you are using IDE in which case there will be a small jumper on the back of the hard drive with the option printed on the drive casing. If you would like me help with this just post back.

---

### Post by azrulyahya77 on 2009-06-22
tarps87

I'm using SATA for both HDD.

---

### Post by sadaruwan12 on 2009-06-22
This is the same thing what I've done it's very simple just go ahead and install Windows XP on which ever drive you want to install it to then install Ubuntu on your other drive and remember on which drive you've installed ubuntu. Now go to BIOS by pressing the relevant key ( on intel or intel chipset boards it's mostly F2 on an AMD chipset or a AMD supported boards it's mostly DEL) and got to the hard disk priority setting and set your Ubuntu installed partition as the firs hard disk and the WinXP one as the secondary hard disk now save changes and let the PC boot you'll GRUB getting loaded with out any trouble.

P.S: it's important that you write down which hard drive you used to install Ubuntu. This happens because Ubuntu installs GRUB in the 1 HDD or the one you're installing Ubuntu in so do the above and you''l go through.

---

### Post by azrulyahya77 on 2009-06-22
Ok..thanks everybody for helping me out :)

---

### Post by tarps87 on 2009-06-23
> **azrulyahya77 said:**
> tarps87

I'm using SATA for both HDD.

Bad guess then :)

---

