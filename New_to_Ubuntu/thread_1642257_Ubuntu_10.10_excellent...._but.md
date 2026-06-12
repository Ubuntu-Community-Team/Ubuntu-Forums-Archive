---
title: "Ubuntu 10.10 excellent.... but"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Kramer2010 on 2010-12-10
Installed 10.10 using wubi and uninstalled it a week later. Reason? could not adjust screen brightness. Tried Fn keys, gnome power management, plus no end of workarounds in the terminal. Great pity as everything else was good to go, but I value my eyesight more.

Think will wait for the next ubuntu build and see if this bug is fixed.

For anyone thats interested, I'm currently running windows 7 premium on a packard bell Easynote TJ68, with a pentium dual core T4400 @ 2.20 GHz and 4mb ram.

The cruncher? ... 

graphics card: Mobile Intel(R) 4 Series Express Chipset Family

---

### Post by gary0 on 2010-12-10
Try installing it along side windows as a dual boot system, rather than installing within windows with wubi. See what you think then... :-)

---

### Post by ronnielsen1 on 2010-12-10
For hardy but should have worked
[http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html](http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html)
>  If you recently installed Ubuntu Hardy Heron 8.04 and discovered that your [laptops]("http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html#")  function keys are not properly adjusting the brightness. In essence,  you are pressing the key combination and nothing is happening try this  fix. 
 Before doing any changes you need to take backup of existing files
 Now you need to [download]("http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html#") the following files in /etc/acpi/ directory
 Download video_brightnessup.sh from [here]("http://www.ubuntugeek.com/images/video_brightnessup.sh")
 Download video_brightnessdown.sh from [here]("http://www.ubuntugeek.com/images/video_brightnessdown.sh")
 After replacing these scripts
 No reboot or logout required, simply press your function combination on your [laptop]("http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html#") to change brightness. Try to press FN + Up/Down Arrow.

or you could have tried this:
[http://mohibuzzaman.blogspot.com/2008/12/brightness-applet-in-intrepid-ibex.html](http://mohibuzzaman.blogspot.com/2008/12/brightness-applet-in-intrepid-ibex.html)

> I was facing problem with lcd brightness applet in my Vaio. This problem  started after upgrading to Intrepid from Hardy. I was on the way of  searching......but...suddenly i found that... there is an option in my  Vaio..which is "Fn+F5,F6"!!! And, yep.. i can work with these three  buttons only!!! :) 

---

### Post by Kramer2010 on 2010-12-10
> **gary0 said:**
> Try installing it along side windows as a dual boot system, rather than installing within windows with wubi. See what you think then... :-)

Do you have evidence/reasoning, that an installation alongside windows will restore control to display brightness?  

I really like Ubuntu but I do not want a lemon that will difficult to remove from my laptop.

FYI, another reason I used wubi was due to only being offered manual partition option rather than the option of Guided automatic partitioning - letting Ubuntu installation process handle partitioning.

---

### Post by Hippytaff on 2010-12-10
Try it with the LiveCD, if it works there then it should work with a 'real' install

---

### Post by Rubi1200 on 2010-12-10
I agree with Hippytaff. Try the LiveCD first including configuring your setup as you would want to have it (not everything might work because it is a CD) and if it works for you, then install to the hard-drive.

Also, if you are using the 10.10 version, there have been changes made to the installer. This means the side-by-side option is no longer available.

However, forum members kansasnoob and Herman have been involved in a discussion about this, including putting together some guides:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
(it's a long post, so you will need to sift through to find what you want)

---

### Post by Kramer2010 on 2010-12-10
> **Rubi1200 said:**
> I agree with Hippytaff. Try the LiveCD first including configuring your setup as you would want to have it (not everything might work because it is a CD) and if it works for you, then install to the hard-drive.

Also, if you are using the 10.10 version, there have been changes made to the installer. This means the side-by-side option is no longer available.

However, forum members kansasnoob and Herman have been involved in a discussion about this, including putting together some guides:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
(it's a long post, so you will need to sift through to find what you want)

Hi just tried 64 bit live cd and i'm afraid the brightness adjustment is still not playing ball..dammit!!!

---

### Post by beew on 2010-12-10
The brightness thing may be hardware related. It doesn't work in one computer but it may work on another one.

This brings me to my next point. Forget about the live CD, CD is yesterday's technology , it is clumsy, clunky and slow and the worst part is you can't store any change, so it is useless if I want to try installing things and that may require a reboot, say. Had I test driven my Ubuntu with a live CD like so many people recommend I would never have installed it in the first place, because performance wise it is horrible.  A live CD sounds like a floppy to my ears these days. :)

If you can boot from usb get at least a live usb _with persistence_. But all live systems don't support system level update and if you need to install proprietary drivers you may be out of luck (mainly graphic cards but may be other things as well)

The best strategy would be to install the whole OS into an external hard disk (you can actually do a full installation in  a flash drive but it would be slow) and then you just plug into your computer and boot off it, you can run a full Ubuntu OS with full speed and all its functionalities without changing anything in your computer (Instead of a castrated version like WUBI, which, incidentally could mess up your native system)

This is also completely portable, you can plug it in any computer provided you don't need proprietary graphic drivers (you can install those as well, only that after you have installed, say, a Nvidia driver you would have to uninstall it if you want to plug it into a different computer that doesn't have a Nvidia card)

So, say, you may have access to another computer and you can plug this in and run a Ubuntu session, and the brightness thing may work on this computer because the hardware is different.

---

### Post by beew on 2010-12-10
Oh, you can also buy a screen to put on your monitor if you have a desktop. A guy at work does that because he couldn't dim the monitor (with Windows XP ) either. :)

---

### Post by Kramer2010 on 2010-12-10
> **beew said:**
> The brightness thing may be hardware related. It doesn't work in one computer but it may work on another one.

This brings me to my next point. Forget about the live CD, CD is yesterday's technology , it is clumsy, clunky and slow and the worst part is you can't store any change, so it is useless if I want to try installing things and that may require a reboot, say. Had I test driven my Ubuntu with a live CD like so many people recommend I would never have installed it in the first place, because performance wise it is horrible.  A live CD sounds like a floppy to my ears these days. :)

If you can boot from usb get at least a live usb _with persistence_. But all live systems don't support system level update and if you need to install proprietary drivers you may be out of luck (mainly graphic cards but may be other things as well)

The best strategy would be to install the whole OS into an external hard disk (you can actually do a full installation in  a flash drive but it would be slow) and then you just plug into your computer and boot off it, you can run a full Ubuntu OS with full speed and all its functionalities without changing anything in your computer (Instead of a castrated version like WUBI, which, incidentally could mess up your native system)

This is also completely portable, you can plug it in any computer provided you don't need proprietary graphic drivers (you can install those as well, only that after you have installed, say, a Nvidia driver you would have to uninstall it if you want to plug it into a different computer that doesn't have a Nvidia card)

So, say, you may have access to another computer and you can plug this in and run a Ubuntu session, and the brightness thing may work on this computer because the hardware is different.

Think i've not done my homework. I booted up live cd and installed ubuntu to an external drive and I cannot get windows or ubuntu to boot....help!!!

---

### Post by Hippytaff on 2010-12-10
open a terminal and do
```

sudo update-grub

```

Should get windows back

---

### Post by beew on 2010-12-10
Ok. I think you might have installed the bootloader into the internal drive. I would have given you more detail instructions if you tell me that you are going ahead to do that. You need to choose "advanced" to decide where you would install the bootloader and you would install it in the external drive.

Try this to get Windows back (you have XP?) Detach the external hard drive. Insert a Windows disk into the CD drive and boot from it, choose repair and then type "fixmbr". Then remove the CD and reboot. This should let you boot into Windows. If you have Windows 7 or Vista the procedure is a bit different.

If you succeed then simply reinstall Ubuntu into the external drive and making sure that you install the bootloader in the external drive.

You should choose "manual" in every step that give you a choice.

Sorry I can't be more specific right now cause I am not home.

---

### Post by beew on 2010-12-10
> **Hippytaff said:**
> open a terminal and do
```

sudo update-grub

```Should get windows back

He couldn't boot into Ubuntu. Moreover, Ubuntu is installed in an external drive, you don't want to have to plug in the external drive everytime he wants to boot into Windows.

---

### Post by Hippytaff on 2010-12-10
I was thinking, do this from the live cd, but your right. The bootscript needs to be run...mbr might have been shafted!?

op - here's the link to the bootscripts to see what is what. Boot from a liveCD, download and run the script and post the results.txt here :-)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Kramer2010 on 2010-12-10
> **Hippytaff said:**
> I was thinking, do this from the live cd, but your right. The bootscript needs to be run...mbr might have been shafted!?

op - here's the link to the bootscripts to see what is what. Boot from a liveCD, download and run the script and post the results.txt here :-)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Hi guys,

Sorry for causing grief, I tend to jump in feet first.  Have repaired Windows 7 using a recovery disc and the command prompt option from my desktop pc.

---

### Post by Hippytaff on 2010-12-10
Feet first is best...swim or drown :-)

so now your mbr will have the windows boot effort in it...if I'm right in thinking your ubuntu is on a separate HDD, plaug it in and now do the boot script thing :-)

---

### Post by Kramer2010 on 2010-12-11
> **Hippytaff said:**
> Feet first is best...swim or drown :-)

so now your mbr will have the windows boot effort in it...if I'm right in thinking your ubuntu is on a separate HDD, plaug it in and now do the boot script thing :-)

Yep ubuntu on 160gig sata drive, was going to try to install it again from live cd again (correctly this time - have instructions). But i'm curious how does the boot script thing work, If I plug in the drive and boot will i get on screen option to select ubuntu or windows?

---

### Post by beew on 2010-12-11
> **Kramer2010 said:**
> Yep ubuntu on 160gig sata drive, was going to try to install it again from live cd again (correctly this time - have instructions). But i'm curious how does the boot script thing work, If I plug in the drive and boot will i get on screen option to select ubuntu or windows?

Yes, if you haven't removed the internal drive while you install Ubuntu in the external drive. When you plug the external drive in the same computer you would be able to choose to boot either into Windows or Ubuntu.

However, a catch is that if you plug the external drive into another computer (not the one you install it with) the Windows boot option would still show up even though Windows is no longer there ( or not the same Windows). So that Windows boot entry is useless if you use the external hdd on a different computer. But I guess it should be ok as long as you don't get confused.

---

### Post by Hippytaff on 2010-12-11
The boot script is just a diagnostic script which shows all partitions, whats on mbr, fstab etc etc. (I say just, it is really useful)

Good luck with the install :-)

---

### Post by Kramer2010 on 2010-12-11
> **beew said:**
> The brightness thing may be hardware related. It doesn't work in one computer but it may work on another one.

This brings me to my next point. Forget about the live CD, CD is yesterday's technology , it is clumsy, clunky and slow and the worst part is you can't store any change, so it is useless if I want to try installing things and that may require a reboot, say. Had I test driven my Ubuntu with a live CD like so many people recommend I would never have installed it in the first place, because performance wise it is horrible.  A live CD sounds like a floppy to my ears these days. :)

If you can boot from usb get at least a live usb _with persistence_. But all live systems don't support system level update and if you need to install proprietary drivers you may be out of luck (mainly graphic cards but may be other things as well)

The best strategy would be to install the whole OS into an external hard disk (you can actually do a full installation in  a flash drive but it would be slow) and then you just plug into your computer and boot off it, you can run a full Ubuntu OS with full speed and all its functionalities without changing anything in your computer (Instead of a castrated version like WUBI, which, incidentally could mess up your native system)

This is also completely portable, you can plug it in any computer provided you don't need proprietary graphic drivers (you can install those as well, only that after you have installed, say, a Nvidia driver you would have to uninstall it if you want to plug it into a different computer that doesn't have a Nvidia card)

So, say, you may have access to another computer and you can plug this in and run a Ubuntu session, and the brightness thing may work on this computer because the hardware is different.

UPDATE!!  Fixed brightness controls using code from this site

[http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html](http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html)

Seen this before but thought it only worked with ACER laptops.

Also gave up on install to ext drive, back on the wubi!!, works fine, lappy boots in 30 secs!

---

### Post by Hippytaff on 2010-12-11
Excellent, glad you got it sorted - remember to mark the thread as solved in the thread tools at the top of the page for others to see what you did to fix the issue

---

