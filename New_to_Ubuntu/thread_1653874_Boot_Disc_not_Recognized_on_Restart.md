---
title: "Boot Disc not Recognized on Restart"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by maryalesia on 2010-12-27
I'm trying to help a friend set up a dual-boot. He seems to be under the impression that I know what I'm doing.

I'm using the same live-CD I used to install Ubuntu 10.04 on my own computer, so it isn't an ISO problem. I changed the BIOS menu so that CDROM was first in line for booting, and still no dice. 

In windows the live CD shows up as an application to install ubuntu. I clicked that and chose the option "install CD boot helper". It installs but then ends with this error message: "could not retrieve installation files". 

What do I do?? I'm not sure what the hardware on this laptop is. It was one of those "pick-your-own-hardware" things.

---

### Post by maryalesia on 2010-12-27
PS - if I choose "manually reboot later" will it install with me needing to boot from the CD? Or no? I don't want to choose the Wubi option because that's just a temporary fix.

---

### Post by davidmohammed on 2010-12-27
when you say "still no dice" - do you mean that it is not attempting to boot from the CD drive just after power-on?  Or is it displaying the purple boot screen before hanging/black screen or something like that?

---

### Post by maryalesia on 2010-12-27
> **davidmohammed said:**
> when you say "still no dice" - do you mean that it is not attempting to boot from the CD drive just after power-on?  Or is it displaying the purple boot screen before hanging/black screen or something like that?

It is not attempting to load from the CD drive. It auto-loads into vista.

---

### Post by wilee-nilee on 2010-12-27
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by davidmohammed on 2010-12-27
you said that the CD worked on your computer but not your friends...

you should at the very least get a couple of CD Drive flashes on boot to indicate that the CD-Drive is OK.  It you dont then maybe the CD Drive is "disabled" from the boot up process ?

May be a CD-R vs CD+r issue - rare if using relatively new equipment.

Otherwise, I would just install via a USB stick.

---

### Post by maryalesia on 2010-12-27
> **davidmohammed said:**
> you said that the CD worked on your computer but not your friends...

you should at the very least get a couple of CD Drive flashes on boot to indicate that the CD-Drive is OK.  It you dont then maybe the CD Drive is "disabled" from the boot up process ?

May be a CD-R vs CD+r issue - rare if using relatively new equipment.

Otherwise, I would just install via a USB stick.

It was disabled, but I changed the BIOS settings so that booting from the CD drive should be the first option the comp goes to. I'm going to do the bootscript thing and if that doesn't work I'm going to try a USB stick.

---

### Post by Malcolm Waterman on 2010-12-27
Test the CD/DVD drive. It's possible there's a malfunction somewhere there. Try these links for information about how to test your drive:
[http://www.computerhope.com/issues/ch001090.htm](http://www.computerhope.com/issues/ch001090.htm)
[http://www.recipester.org/Recipe:Test_DVD_Drive_or_DVD_Burner_27480332](http://www.recipester.org/Recipe:Test_DVD_Drive_or_DVD_Burner_27480332)

Note about the second URL, Nero provides other tools designed for diagnostic purposes. You can try downloading a trial of the software from [http://www.nero.com.]("http://www.nero.com/")

---

### Post by Malcolm Waterman on 2010-12-27
Just a thought, I had some problems getting Ubuntu to start up initially. Different symptoms, but perhaps the same cause. In the BIOS there might be a setting called "Enable Legacy USB support." On my system that was disabled, though when it was enabled Linux did start to work.

---

### Post by maryalesia on 2010-12-27
> **Malcolm Waterman said:**
> Just a thought, I had some problems getting Ubuntu to start up initially. Different symptoms, but perhaps the same cause. In the BIOS there might be a setting called "Enable Legacy USB support." On my system that was disabled, though when it was enabled Linux did start to work.

I'm making a USB boot now, but if that doesn't work I will def try that.:D

---

### Post by maryalesia on 2010-12-27
the USB boot stick didn't work.

---

### Post by maryalesia on 2010-12-27
wait no it did! I changed the bios settings menu to include every USB option there was and put all of those options ahead of what I assumed was windows.:D

---

