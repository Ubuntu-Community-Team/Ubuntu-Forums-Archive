---
title: "Absolute beginner"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Carbonara on 2011-08-24
Hi there,

I just learned about the Ubuntu, and is trying to download one into my windows7.

I am using the Wubi now, during the installation process, it asked me to opt for the place to install while I have a few partitions in my harddisk. I just wonder should I install it in the C: drive or should I install in other partition? thanks.

---

### Post by Rex Bouwense on 2011-08-24
Since WUBI is meant for an introduction to Ubuntu, you will either be uninstalling it because you do not like it or doing a real dual boot in the near future because you do.  You can install it on an extended partition or anywhere you like.  See:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
:popcorn:

---

### Post by Carbonara on 2011-08-24
Thanks, and what is the optimal installation size I should allocate for Ubuntu?

---

### Post by Rex Bouwense on 2011-08-24
I believe that the maximum is 30 Gbs if installed with WUBI.

---

### Post by Carbonara on 2011-08-24
thanks, and actually what is the difference between the Wubi and the real dual boot? 

I can see at this link, it says Wubi can runs with windows.
And would like to know if the first option "download and install" id the dual boot that you've mentioned ?
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

As my desktop will be share with my other family members using the Win7, if I download a 64-bit from the first option "download and install", can it run with window7 too?

---

### Post by MG&amp;TL on 2011-08-24
As I understand it, WUBI is a 'program' that runs in windows, whereas a dual-boot actually partitions your harddrive and installs a bootloader so you can choose between the two. WUBI, however, is not the most stable thing on the planet, so I would suggest booting from USB or VirtualBox instead. Until you want a dual-boot. :)

---

### Post by sffvba[e0rt on 2011-08-24
The main difference between installing Ubuntu via WUBI vs installing it in a traditional dual boot configuration is that with WUBI Ubuntu is installed in a image file created and stored on a Windows native partition and not an a native Linux partitioning scheme.

So in theory I guess it may be a bit slower (and I think you may loose some of the more advanced features on files... but they are not needed for casual users like us :))

Once installed through either WUBI or as a dual boot you will have to reboot the computer, at which time you can choose if you want to run Ubuntu, or run Windows.  It will then boot into that OS for you to use.

The convenience of WUBI is you can undo the Ubuntu install easily from within Windows the same way you uninstall any installed program :)



404

---

### Post by MG&amp;TL on 2011-08-24
The first two options shown there are images to burn to a cd or USB so that you can dual-boot, try ubuntu from the stick/CD, or replace your OS.

The third is WUBI.

---

### Post by fdrake on 2011-08-24
> **Carbonara said:**
> thanks, and actually what is the difference between the Wubi and the real dual boot? 

I can see at this link, it says Wubi can runs with windows.
And would like to know if the first option "download and install" id the dual boot that you've mentioned ?
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

As my desktop will be share with my other family members using the Win7, if I download a 64-bit from the first option "download and install", can it run with window7 too?

with wubi you don't have a linux partitions, everything is inside the win partition. so if you have problem with your win partition you will have problem with ubuntu too

---

### Post by Carbonara on 2011-08-24
thanks all,

If I boot from a USB, will the speed of USB affect the speed of the system?

---

### Post by sffvba[e0rt on 2011-08-24
Yup.

The speed of the USB will be the limiting factor.  But it is still plenty fast to give a good indication of how well Ubuntu works. 


404

---

### Post by MG&amp;TL on 2011-08-24
A little. But not very much. USBs are very fast. It depends on how fast your system was to start with, and tbh, unless you have a SERIOUS PC, I doubt that it will make much difference.

 EDIT: IMO, anyway, 404. :)

---

### Post by Carbonara on 2011-08-24
thanks all,

Since my family would have to use the Win7 as they may not interested in learning a new system, therefore i can't replace the Win7 OS.


so i guess I will try the Wubi as well as the dual bool from the USB, so I can compare :)

---

### Post by sffvba[e0rt on 2011-08-24
Good luck and enjoy it :)


404

---

### Post by Carbonara on 2011-08-24
Thanks :)

---

### Post by MG&amp;TL on 2011-08-24
Oh, and if you do decide to dual-boot, backup your files first. Partitioning is a big shock to the system, so WEIRDNESS MAY OCCUR in various forms (from slight loss of sound in some places, to total non-booting), but this is getting rarer and rarer for Ubuntu. Best of luck, and away you go! :D

---

### Post by Carbonara on 2011-08-24
thanks, i guess I will set aside a new USB for the Dual boot then.

for the Wubi to be install in my harddisk, can I delete the exe. file after I install the programme?

---

### Post by MG&amp;TL on 2011-08-24
IDK, personally I wouldn't unless disk space is a real issue. When you get fed up with WUBI, you can remove it along with the uninstall.

---

### Post by Carbonara on 2011-08-24
ok i see, so i'm gonna reboot now :) 
thanks so much for you help !

---

### Post by MG&amp;TL on 2011-08-24
Good luck! I hope we have  a satisfied customer...

---

