---
title: "installing a windows driver"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by chuning on 2010-09-08
Hello - I'm trying to install the driver for a Trust graphics tablet on Ubuntu 10.04, without much success.

I have the .exe file sitting in my download folder, but not quite sure what to do now.

Any help much appreciated

Chris

---

### Post by Achilles124 on 2010-09-08
You cannot install a windows driver on a Linux system. Period.

---

### Post by chuning on 2010-09-08
Sorry, maybe I put it the wrong way.

Before I bought the graphics tablet (Trust mini widescreen 16485), which comes with only Windows and Mac drivers), I searched various reviews etc., and found various that said they had managed to get the drivers working after some fiddling around.  Would this be via Wine, or something like that?

---

### Post by mapes12 on 2010-09-08
> Before I bought the graphics tablet (Trust mini widescreen 16485), which comes with only Windows and Mac drivers), I searched various reviews etc., and found various that said they had managed to get the drivers working after some fiddling around. Would this be via Wine, or something like that?As Achilles124 said win drivers will not work in Linux. Driver support is either compiled in the kernel or it isn't. If it doesn't work "out of the box" your only hope to get it working is:-

1. Google for a work around
2. Contact the manufacturer and ask how the hardware is supported on the Linux platform and for step by step instructions.

---

### Post by Mark Phelps on 2010-09-08
> **chuning said:**
> Would this be via Wine, or something like that?
Sorry, no.  Despite what you may have been told by others, Wine can NOT be used to install MS Windows drivers, only to run SOME MS Windows applications.

The lone exception is that, in some cases, MS Windows drivers can be used for networking -- but that has nothing to do with your current issue.

---

### Post by sikander3786 on 2010-09-08
Cannot install Windows driver in Linux, made clear in the posts above.

Still tell us a little more about your situation. What have you got and what you want to accomplish, might be you get some good advice.

Furthermore this link might also help.

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

### Post by chuning on 2010-09-09
Thanks for all the answers - I'm relatively new to Linux, so am floundering around a bit.

I have a netbook that i have installed Ubuntu 10.04 on, and like it very much.  I have bought a Trust Mini Widescreen 16485 tablet as a travelling version of the Wacom tablet I use at home.

I have just discovered that this tablet is made by Waltop, who do have a Linux driver on their website.  I've downloaded this, and am now feeling rather foolish because I have forgotten how to install it.  Can someone remind me?

Many thanks

---

### Post by mapes12 on 2010-09-09
Please can you post the link to the driver so that we can take a look at it.

---

### Post by Achilles124 on 2010-09-09
This is a review on the Amazon.com website:

> Trust Widescreen Mini Tablet works fine on GNU/Linux Debian without configure it like a tablet and mouse pointer.
It was tested with design apps like GIMP and Krita.

On the other hand, on Microsoft Windows was necessary to calibrate the device several times until their behavior was appropriate.

The virtual keys of the device are useful if you do not use all the drawing space. If not your case, disable this feature.


So, according to this guy, it works out of the box. 

If not, then you must make use of the driver you have found. Probably, a tar.gz file. So, ./configure, make, make install. Look for more information on the net.

---

### Post by chuning on 2010-09-09
The link to that driver is [http://www.waltop.com.tw/download.asp](http://www.waltop.com.tw/download.asp)

It does work to an extent out of the box, but not a very great extent - no pressure sensitivity or anything, the pen moves the cursor is all (and that slightly reluctantly when the pen is not actually touching the pad)

---

### Post by Favux on 2010-09-10
Hi chuning,

The plan is for the Waltop's to work on the Wacom driver (xf86-input-wacom).  But there's been a problem with the usb hid kernel part of the Waltop drivers.  So folks have been using the WizardPen Driver instead.

Go to Synaptic Package Manager and enter wizardpen in the QuickSearch bar.  Install the package called xserver-xorg-input-wizardpen.  Right-click on it and check Mark for Installation, and then the to Apply button.  Use my 70-wizardpen.conf file in post #5 here:  [http://ubuntuforums.org/showthread.php?t=1528329](http://ubuntuforums.org/showthread.php?t=1528329)  DoctorMo also has a ppa for the WizardPen driver if needed.

The good news is a developer is submitting patches for the hid-waltop.ko to the kernel so it looks like the Wacom drivers will work for the Waltop shortly.

---

