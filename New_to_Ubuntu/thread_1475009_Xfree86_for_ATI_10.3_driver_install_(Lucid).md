---
title: "Xfree86 for ATI 10.3 driver install (Lucid)"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Ageek on 2010-05-06
I have read all the install instructions from ATI for installing the 10.3 driver on Lucid.

It says that I am required to have the following packages installed:

XFree86-Mesa-libGL
libstdc++
libgcc
XFree86-libs
fontconfig
freetype
zlib
gcc

I have most installed and can verify there version.
I do not have XFree86-Mesa-libGL or XFree86-libs installed and I cannot figure out how to install them. I looked in the Ubuntu Software Center and the Synaptic Package Manager but I am not able to find them.

Can someone please tell me where to find these packages?

---

### Post by e4uforums on 2010-05-06
Try this:

[http://ubuntuforums.org/showthread.php?t=206285](http://ubuntuforums.org/showthread.php?t=206285)

---

### Post by shebaw on 2010-05-06
The driver they released for Lucid is 10.04 not 10.03 so try downloading that.

---

### Post by QIII on 2010-05-06
Don't bother downloading it.

The driver is available in the repos.

Install it from Synaptic.  While you're there, install the Catalyst Control Center.

---

### Post by Ageek on 2010-05-06
Thanks for the reply.

I found that post earlier and read through everything on it several times.

It still does not tell me where to find those 2 packages I need to install before I do the driver install.

I looked at the Xfree website for install instructions but I will admit  that was over my head. I have no idea what they were trying to say with  the install instructions.

Any other ideas?

---

### Post by Ageek on 2010-05-06
Sorry about that. It is version 10.4.

The name of the driver is: [B]ATI Catalyst™ 10.3 Proprietary Linux x86 Display Driver
[/B][FONT=Verdana]But it says Revision Number: 10.4


I cannot find it in Synaptic Package Manger. Is it under another name and do I still need to install the Xfree86 in order to use that one?

Thank again for the help everyone!
[/FONT]

---

### Post by QIII on 2010-05-06
The Synaptic Package Manager is an application in your Ubuntu OS.

Go to System | Administration | Synaptic Package Manager.

You will have to enter your login password.  When it is open, there is a search field. I think you should find what you want by searching for "fglrx".

(I'm not at my Ubuntu machine right now, unfortunately...)

Look for something described as the "driver" and another described as "Catalyst Control Center" and select both.  Click apply.

The advantage of using Synaptic are (at least) two-fold:  You get a GUI interface until you have mastered the terminal, and any dependencies will automatically be installed as needed.

---

### Post by Ageek on 2010-05-06
I found the fglrx driver in Synaptic Package Manager but it said it was for 2D only. I was using the ATI driver so I could have my 3D running. 
If I install fglrx will it install all the Xfree86 items I need to install the ATI driver for my 3D?

---

### Post by QIII on 2010-05-06
I'm not at my Ubuntu machine right now.

One of my machines is a Lucid machine running the ATI 10.4 driver and using Catalyst Control Center with 3D and visual effects enabled.   I installed everything from the repos.

If you can wait a few hours until I get home from work, I can tell you exactly what to do...

---

### Post by Ageek on 2010-05-06
Sure thats no problem. Thanks for the help.

---

### Post by Ageek on 2010-05-06
I can install the ATI fglrx drivers by going to System / Administration / Hardware Drivers.

Can I install those and then use the ATI 10.4 driver to build the .deb packages to get full 3d?

---

### Post by QIII on 2010-05-06
No need to do anything more outside of Ubuntu.  But wait for me to get home to see if that's the best way to do it.

You should get full 3D by installing the way you suggested.  I didn't have to do anything special outside of installing what I found in Ubuntu.

But you will need to go to the terminal and execute

```
sudo aticonfig --initial -f
``` as soon as you do that, or things may get hairy.

Also, install Catalyst Control Center (if it does not install with the driver) so you can make any adjustments through the Catalyst GUI.

Remember that the driver will not be active until the next time you reboot.


Edit:  I remembered that I had filed a bug in launchpad shortly after the driver was posted to the repos.

Yes.  You should be able to install it via Hardware Drivers, and you need to remember to go to the terminal and type the above immediately after installing it.

---

### Post by Ageek on 2010-05-06
Everything worked just like you said it would. Even the CCC installed.

Thanks for all the help everyone and especially QIII !

---

