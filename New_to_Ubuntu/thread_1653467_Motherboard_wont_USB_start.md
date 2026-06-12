---
title: "Motherboard wont USB start"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by sarum on 2010-12-26
Hi, I've a newish computer on which I installed Ubnutu 10.4 as the only OS.
My other OS is Puppy which I use by putting in a live CD when ever I want and I adjusted the BIOS to cope with it. I've now installed Puppy to a USB stick (easier to use than a CD). The BIOS, under 'Boot', has 3 options; HD:CD:USB device. I cannot get the USB to boot; I've tried all combinations, and the USB stick works on my other computer(which has now been sold). Has anyone any idea of what I'm doing wrong, please.
Main Board:-   ASUS P7H55 M LGA1156 H55 DDR3 Motherboard.
Thanks in advance....sarum

---

### Post by Spencer Caplan on 2010-12-26
Hm, my only thought is to make sure that the USB drive containing Puppy Linux is bootable. See if the USB drive will boot to Puppy Linux on another machine, because the drive may have all of the files but not be recognized bootable.

---

### Post by presence1960 on 2010-12-26
I have a Biostar mobo and when I boot a USB stick I have to go into BIOS and under hard disk boot order make the USB first or hit F9 and choose the USB stick to boot. Don't ask me why, but all USB flash disks get classified as a hard disk in my BIOS. However my USB hard disks show up in USB (Removable). Go figure! Check your BIOS again.

---

### Post by garvinrick4 on 2010-12-26
Keep looking around bios to find where you can pick which you want at every boot 
instead of setting defaults in bios. 90 % there somewhere. Got one esc, one f9 one f10 and 
then have to click on hdd and gives me another menu. 4 machines 4 different bios, keep looking
or find type of bios and google manual.

---

### Post by amjjawad on 2010-12-26
> **sarum said:**
> Hi, I've a newish computer on which I installed Ubnutu 10.4 as the only OS.
My other OS is Puppy which I use by putting in a live CD when ever I want and I adjusted the BIOS to cope with it. I've now installed Puppy to a USB stick (easier to use than a CD). The BIOS, under 'Boot', has 3 options; HD:CD:USB device. I cannot get the USB to boot; I've tried all combinations, and the USB stick works on my other computer(which has now been sold). Has anyone any idea of what I'm doing wrong, please.
Main Board:-   ASUS P7H55 M LGA1156 H55 DDR3 Motherboard.
Thanks in advance....sarum

Your USB must be plugged in before you enter BIOS.
Try that. If it did not work, try to read your Motherboard Manual.
If it's new Motherboard, there must be an option for that. My 6 years old MB does have that options.

If not, try this as the last solution: [http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/](http://blog.brothersoft.com/2008/12/09/boot-computer-from-usb-or-cdrom-even-if-bios-not-supported-using-plop/)



Edit:
As per my BIOS, this is how it looks like when USB is plugged in before I enter BIOS:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]

---

### Post by sarum on 2010-12-27
Thanks for your replies - I tried them all except PLoP Linux which is taking forever to load on my machine.While searching other posts, there is one saying that my edition of Puppy(5.10, based on Ubuntu Lucid) wont work from a USB stick; there's a hack, but too complicated for me. So I cut another USB of an older version(Puppy 4.10). Both work fine on another computer. I shall keep trying and post 'solved' whenever. Plop should be here soon. Another suggestion(see above)was to read the main board manual, I shall get on to that now. Cheers......sarum

---

### Post by amjjawad on 2010-12-27
> **sarum said:**
> I tried them all except PLoP Linux which is taking forever to load on my machine.

It shouldn't take forever. I tired it on P2 with 64MB RAM (12 years old laptop) and it worked very fast.

> Another suggestion(see above)was to read the main board manual, I shall get on to that now. Cheers......sarum
Yes, just try that ;)

If you need anything, let us know!

---

