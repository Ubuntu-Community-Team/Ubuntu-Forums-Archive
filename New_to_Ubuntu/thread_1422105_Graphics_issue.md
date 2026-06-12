---
title: "Graphics issue"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-03-05
I have a Dell Inspiron 1525 laptop with Karmik(jaunty upgraded).
I am facing problems enabling the Extra in the Visual Effects under appearance settings.Whenever I select Extra effects it just says:"Desktop effects could not be enabled."
What is the problem and how do I solve it?

---

### Post by Fire_Chief on 2010-03-05
Essentially you have one of two problems.
Either (1) your graphics chipset is not powerful enough to run the Extra desktop effects settings or (2) you have a sufficient chipset but don't have the drivers install to enable the full use of the graphics card capabilities.

In case #1, you're kinda stuck since laptops don't give you the option to upgrade the video card.

In case #2, you can check to see if you have the drivers installed for your (ATI/Nvidia/some Intel) graphics card. I wouldn't count on too much luck with the Intel video cards but an ATI or NVidia should work just fine.

If you do have an ATI or NVidia card, you can look in the Restricted Hardware admin panel and see if the driver is loaded or you can download and use Envy-NG to get the currently available driver installed and working.

Cheers!

---

### Post by peace.gangsta on 2010-03-05
abhinav@abhinav-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

abhinav@abhinav-laptop:~$

---

### Post by Fire_Chief on 2010-03-05
Here's a site that may help you get compiz (extra effects) working.
[http://www.rudkin.me.uk/2009/04/22/how-to-get-your-intel-gm965gl960-working-with-compiz-on-ubuntu-jaunty-jackalope/]("http://www.rudkin.me.uk/2009/04/22/how-to-get-your-intel-gm965gl960-working-with-compiz-on-ubuntu-jaunty-jackalope/")
Don't worry that it's for the previous version of Ubuntu in this case. It should work fine. Note that this may cause some performance DECREASE for video or flash stuff and you *may* have occasional freezes. But many report things working just fine so YMMV.

Cheers!

---

### Post by peace.gangsta on 2010-03-05
Even my mouse pad has stopped functioning ..
I did an upgrade from jaunty to karmik yesterday.All the problems started from there.The first time I started karmik my computer froze.This happened a couple of times more.Finally I restarted and selected a previously installed kernel.I have intel media accelerator . It used to support desktop cube and other animations on jaunty.SO I don't think the problem is with the hardware.I suppose the problem might have risen cause of the upgrade.
Is there any solution.
Thanks in advance

---

### Post by Fire_Chief on 2010-03-05
Ah, the curse of the upgrade path. #-o

I know it's supposed to be a supported method but I've seen and heard way too many problems from upgrades to ever recommend it. I usually do a clean install instead of upgrade. To make it simpler, either backup your /home folder data for your user account(s) and then install Karmic or partition /home into its own partition away from the rest of the OS. Then you can clean install an OS and not lose the data at all (assuming you tell it not to format the /home partition).

Cheers!

---

### Post by peace.gangsta on 2010-03-05
The compiz runs now but my wireless stopped functioning.
Ahh what the hell I am formatting.
See you in a couple of hours :P

---

