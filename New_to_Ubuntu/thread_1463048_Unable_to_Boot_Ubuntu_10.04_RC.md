---
title: "Unable to Boot Ubuntu 10.04 RC"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by ravi_buz on 2010-04-26
I downloaded Ubuntu 10.04 RC few days back and burned it into a Cd and tried booting from it. After few minutes it showed an error and the cd was ejected. I booted using ubuntu 9.10 and created a usb startup disc of 10.04 and tried booting from pen drive and ubuntu 10.04 was loading for 30min and never came to the installation part. I tried both the CD and Pen drive on a laptop and both worked perfectly. Then i removed all my hardware and booted onl with CD  then only with the USB drive and nothing happened . So can any one of you guys tell me what the problem is .:confused: I currently have Win7 in my desktop.

---

### Post by Mikeoak on 2010-04-26
> **ravi_buz said:**
> I downloaded Ubuntu 10.04 RC few days back and burned it into a Cd and tried booting from it. After few minutes it showed an error and the cd was ejected. I booted using ubuntu 9.10 and created a usb startup disc of 10.04 and tried booting from pen drive and ubuntu 10.04 was loading for 30min and never came to the installation part. I tried both the CD and Pen drive on a laptop and both worked perfectly. Then i removed all my hardware and booted onl with CD  then only with the USB drive and nothing happened . So can any one of you guys tell me what the problem is .:confused: I currently have Win7 in my desktop.

I can't boot the CD either, been having problems after Beta 1.  Same thing with Kubuntu.  I just get a blank screen like the computer is looking for something to boot then the computer gives up and boots back to my Mint 8 install on HD.

I burned the CD at the lowest speed.  My computer is a Gateway Computer, Quad CPU, AMD 64.

---

### Post by -humanaut- on 2010-04-26
Are either of you using proprietary video cards? It seems the new plymouth loader doesn't really display them try downloading the Daily-Build of the R.C. it has newer x11 plymouth boot files might help.

---

### Post by ravi_buz on 2010-04-26
i tried the CD on my laptop and it worked perfectly.. so there is no problem with the CD then tried ubuntu 9.10 on my desktop and it booted and worked fine so there is no problem with my system.

---

### Post by Hospadar on 2010-04-26
I would try booting with the alternate installer image (do it off your thumb drive first to save disks).  The "alternate" is an all-text installer (although it installs the regular desktop system), and can sometimes:

a) boot when the regular livecd doesn't if there are some video problems (since the alternate is text-only)

b) sometimes will show more helpful error messages since it isn't designed to be as good-looking and user-friendly as the regular livecd

Another option may be to disable "quiet" booting and the bootsplash to try and get ubuntu to show all the bootup messages.

When you boot with the livecd I think there's some way to change the boot entries/kernel options.  You'll want to remove "quiet", and I think you either remove "splash" or add "nosplash", you can play around and see what works.

---

### Post by ravi_buz on 2010-04-30
hey guys just downloaded the final release and still the problem is there , is this a bug!!! can some one help me pls

---

### Post by Peter09 on 2010-04-30
You need to do as Hospadar suggested, boot without the quiet option, that will tell you where things are going wrong and give us a clue as how to fix it.

---

### Post by zipperback on 2010-04-30
To make sure that there aren't any problems with the .iso you downloaded, you should check the md5checksum.

Also you should do a media verification before trying to actually install the distro.

Both of these things will be of a great help to ensuring your system isn't dealing with a set of corrupted installation files.

- zipperback
:popcorn:

---

### Post by ravi_buz on 2010-04-30
the iso is fine as i am able to boot it and get into the live session mode in my laptop.
i think i found the solution in the office website which explains the problem and the solution. will try that when i go home and will put the result.

@above.how can i disable the silent boot mode

---

### Post by Peter09 on 2010-04-30
Hold the shift key during boot, that should get you into a menu, details I forget, which should contain an option to edit the grub boot parameters (temporarily) remove the option **quiet** and change **splash** to nosplash and the allow the machine to boot.
 
Sorry I cannot be more specific as I'm not near a machine.

---

