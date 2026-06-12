---
title: "Upgrade to 11.04"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Churchwarden on 2011-05-03
I tried the automatic upgrade path.  All appeared to go smoothly for about six hours until the restart.  Then the usual OS select screen came up.  I selected Ubuntu and all I got was a faintly illuminated screen a little non flashing cursor in the top left of the screen and a caret near to the middle of the screen.  I left it overnight hoping that it would do something.  It didn't.

Is the best thing at this stage to reinstall from scratch?

TIA

Nick

---

### Post by jtarin on 2011-05-03
Are you dual booting? Did you ever see the Grub screen to choose a kernel?

---

### Post by ravi_buz on 2011-05-03
Maybe the drivers are not installed/compatible with 11.04. When booting select the recovery option and within it select low graphic mode and select ubuntu classic instead of Ubuntu and set it as default and restart your system.

Now if your able to access the system and everything works fine you might start by installing the necessary drivers required to get unity working.

---

### Post by Churchwarden on 2011-05-03
I have a DVD with the new version of Ubuntu.  I thought that I would do a complete reinstall using that.  A screen towards the beginning of the process says that I can install alongside "multiple operating systems".  What I wold like to do is to remove the last version of Ubuntu but leave Vista in place.  what would I need to do to achieve this?

All the best

N

---

### Post by Churchwarden on 2011-05-03
> **jtarin said:**
> Are you dual booting? Did you ever see the Grub screen to choose a kernel?

sorry to be lacking in knowledge.  what's the Grub screen?

N

---

### Post by Churchwarden on 2011-05-03
> **ravi_buz said:**
> Maybe the drivers are not installed/compatible with 11.04. When booting select the recovery option and within it select low graphic mode and select ubuntu classic instead of Ubuntu and set it as default and restart your system.

Now if your able to access the system and everything works fine you might start by installing the necessary drivers required to get unity working.

I could not access the system at all.  It froze before getting to the desktop.

N

---

### Post by rez182 on 2011-05-03
> **Churchwarden said:**
> What I wold like to do is to remove the last version of Ubuntu but leave Vista in place.  what would I need to do to achieve this?

All the best

N

i have a similar problem as you, its probably the my nvidia graphics driver that is not compatible with unity. and nobody replies in my thread either.. if someone can help plz view [http://ubuntuforums.org/showthread.php?t=1747784](http://ubuntuforums.org/showthread.php?t=1747784)

and the way to achive what your looking for the best and safest way i found was to use your vista to delete the ubuntu and ubuntu swap partitions and leave it unallocated and then just select install alongside windows. it will automatically create swap and etc... i prefer you use easeus partition master home edition, its free.

---

### Post by ManiDhillon on 2011-05-03
> **Churchwarden said:**
> sorry to be lacking in knowledge.  what's the Grub screen?

Grub is the main boot menu which appear when you start your computer. It give you the choice to start(boot) the operating system of your choice from your multi-boot.

And yes you can install Ubuntu alongside Vista and have the previous version erased. It is easy. When on partition/install screen of you live install cd/dvd/usb, select the last option saying something like "Do Something Else". Now choose the partition where you have installed previous version of ubuntu, select edit/change, then choose file system(in my case EXT4) select the tick box saying "format", select the mount path as "/" means root and click ok. Then click the install button. You are done.

---

### Post by rez182 on 2011-05-03
> **Churchwarden said:**
> I could not access the system at all.  It froze before getting to the desktop.

N

ubuntu downloads the drivers while in the installation process. you can check it by clicking show details

---

### Post by Churchwarden on 2011-05-03
> **ManiDhillon said:**
> Grub is the main boot menu which appear when you start your computer. It give you the choice to start(boot) the operating system of your choice from your multi-boot.

And yes you can install Ubuntu alongside Vista and have the previous version erased. It is easy. When on partition/install screen of you live install cd/dvd/usb, select the last option saying something like "Do Something Else". Now choose the partition where you have installed previous version of ubuntu, select edit/change, then choose file system(in my case EXT4) select the tick box saying "format", select the mount path as "/" means root and click ok. Then click the install button. You are done.

Doing that now and keeping my fingers crossed!

All is proceeding as it should...

N

---

### Post by ManiDhillon on 2011-05-03
Don't worry, everything will be okay.

---

### Post by Churchwarden on 2011-05-03
Thanks to all who suggested solutions.

All is now working as it should.

N

---

### Post by Churchwarden on 2011-05-06
> **Churchwarden said:**
> Doing that now and keeping my fingers crossed!

All is proceeding as it should...

N

It all did proceed and the new Ubuntu is working fine.

Thanks to all.

Nick

---

### Post by Fraoch on 2011-05-06
Would you mind marking the thread as "solved"?

Thanks.

---

