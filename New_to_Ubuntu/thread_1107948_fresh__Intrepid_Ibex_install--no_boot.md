---
title: "fresh  Intrepid Ibex install--no boot"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by harley1 on 2009-03-27
Hello, 
 I am an absolute Linux virgin. I downloaded the 8.1 version and verified with the MD5. I loaded it onto my pc  (Gateway with Intel Celeron processor 2.5G 750M ram and 160g HDD). The problem is that the program will not boot. With the disc in the drive, I get to the username/password screen and then after entering them, I just get a blank tan screen. With the disc removed form the tray and trying to boot from the HDD, I get a black screen of death and a moveable cursor.  I am completely new to this and have no idea where to go form here. Any help would be GREATLY appreciated

Thanks 
harley1

---

### Post by BOZG on 2009-03-27
That sounds like a problem with your graphics card and xorg configuration.  What type of card are you using?

When you get to the GRUB menu, try selecting the safe version and letting it boot.  A window should eventually appear with the option to Fix X.  Follow the commands in there and try rebooting.

---

### Post by jbrown96 on 2009-03-27
> **harley1 said:**
> Hello, 
 I am an absolute Linux virgin. I downloaded the 8.1 version and verified with the MD5. I loaded it onto my pc  (Gateway with Intel Celeron processor 2.5G 750M ram and 160g HDD). The problem is that the program will not boot. With the disc in the drive, I get to the username/password screen and then after entering them, I just get a blank tan screen. With the disc removed form the tray and trying to boot from the HDD, I get a black screen of death and a moveable cursor.  I am completely new to this and have no idea where to go form here. Any help would be GREATLY appreciated

Thanks 
harley1

Try starting X manually and see if that helps. When your computer boots, you should see some messages about GrUB. You may need to press Esc, but you should get a listing of available kernels to boot (it will have numbers like 2.6.27-11). Highlight the first one and press E. Then go to the second line and press E again. Now you should be able to edit this line. Add "single" (no quotes) to the end and press B and then maybe B again. The computer should now boot and give you a command line login. It would help if you could get some more information about your computer. Could you post the output of the following commands ```
lspci | grep VGA
``` and ```
cat /etc/X11/xorg.conf | grep Driver
```. Then try to launch a graphical system with ```
startx
``` What happens?

---

### Post by harley1 on 2009-03-27
Thanks Boz I will try that !

---

### Post by harley1 on 2009-03-27
Hey thanks Jbrown, I have a feeling that I may be posting here often, so I will try what you have suggested
Thanks
harley1

---

### Post by harley1 on 2009-03-30
Hello Jbrown,

     I tried the things you said to try, but I got no output when I entered the code you suggested. I do now think tho that the system will boot, because when I got to the login screen, the clock time was correct. I have a G845 Invidia video card and a generic flat panel monitor. the processor is a Celeron @ 2.4Ghz, the hard drive is a Western Digital 160G IDE. I really am not familiar with entering code to change settings, so any extrapolation of the process would help me a lot such as how to get to the screen where the command line is entered and such.
     I was able to load and older version of RedHat Linux (from 2004) and it ran fine, so maybe I just need to tweek some settings to get this latest version of Ubuntu to run. I sure hope that is all it is, otherwise I am looking to purchase a new computer and try to load Linux on that.

Thanks for your help

harley1

---

### Post by harley1 on 2009-03-31
Thanks BOZG and JBROWN-kinda left me hanging after my reply that I couldn't get any code to work. I wonder if I really want Linux at all if it is this difficult to install--I mean for cripes sakes SOMEONE has to have had this problem before----------

harley1

---

