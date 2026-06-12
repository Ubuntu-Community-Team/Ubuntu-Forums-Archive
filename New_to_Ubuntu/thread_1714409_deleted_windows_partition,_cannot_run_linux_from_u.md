---
title: "deleted windows partition, cannot run linux from usb"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by marcussive on 2011-03-25
[COLOR=Black]Hello, I am a reformed apple user, new to linux and pcs/windows.
[/COLOR]
  [COLOR=Black]I was successfully dual booting Win 7 and Ubuntu 32bit on my new Asus N53J. I recently removed Ubuntu 32bit to upgrade to the 64 bit version and [/COLOR][COLOR=Black]mistakenly deleted a critical boot partition where Ubuntu was installed. I was able to partially repair the Win 7 side with all manner of bootfix/repair/etc  (I can boot into a temporary profile but [/COLOR][COLOR=Black]Windows tells me that ‘NLS is missing or corrupted’).[/COLOR]
  [COLOR=Black]BUT, I cannot boot/run/install ubuntu (or Mint or Fedora). I get to the linux start screen with the options to (try, install, verify usb, etc.) but choosing any of these options does nothing and I have to power off.[/COLOR]
  [COLOR=Black]Asus will not provide any kind of re-install disk and wants me to send in the laptop but I’m afraid I might have voided the warranty by installing ubuntu(?).[/COLOR]
  [COLOR=Black]I have lost no data and [/COLOR][COLOR=Black]am happy to trash Win altogether but I am stuck.[/COLOR]
**Thank you for any suggestions!**

---

### Post by blind2314 on 2011-03-25
Instead of trying to boot/install of a USB device, why don't you try downloading and burning the Ubuntu ISO onto a CD? Then you can boot off that. If you don't mind losing windows, just do a clean install and let it blow everything away.

---

### Post by marcussive on 2011-03-25
I tired that but the live cd does the same as usb: [COLOR=Black]I get to the linux start screen with the options to  (try, install, verify usb, etc.) but choosing any of these options does  nothing and I have to power off.
I would LOVE to just wipe all and start clean but I think there is some low level windows boot info that I need to keep.
[/COLOR]

---

### Post by oldfred on 2011-03-25
You have video issues & I do not know if there are workarounds, yet or not:

The Nvidia site explains why: 

*Note that the list of supported GPU products is provided to  indicate which GPUs are supported by a particular driver version. Some  designs incorporating supported GPUs may not be compatible with the  NVIDIA Linux driver: **in particular, notebook and all-in-one  desktop designs with switchable (hybrid) or Optimus graphics will not  work if means to disable the integrated graphics in hardware are not  available. Hardware designs will vary from manufacturer to manufacturer,  so please consult with a system's manufacturer to determine whether  that particular system is compatible.***

---

### Post by blind2314 on 2011-03-25
I can assure you that if you want to ONLY use Ubuntu on this machine, there is no "low level windows boot info" that needs to be kept. :)

---

### Post by marcussive on 2011-03-25
blind2314: How can I install ubuntu?

[oldfred]("http://ubuntuforums.org/member.php?u=852711"): Thanks, but I know that and that's a different topic.

---

### Post by oldfred on 2011-03-25
Often the solution is parameters for setting video.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Some with nVidia chips (not full video cards) said the generic settings worked.

---

### Post by blind2314 on 2011-03-25
> **marcussive said:**
> blind2314: How can I install ubuntu?
 
[oldfred]("http://ubuntuforums.org/member.php?u=852711"): Thanks, but I know that and that's a different topic.
 
 
Burn a Live CD for ubuntu (you can download the .iso from their main page, ubuntu.com), and boot from it. There should be options to try ubuntu, or install. You can choose install, and then follow the guided process throughout.

---

### Post by marcussive on 2011-03-25
blind: maybe you are blind? I repeat: I CANNOT boot linux from USB key or Live CD. I see the options to try, install, etc. but I CANNOT get past this menu.
If anyone knows of ANOTHER way to install linux, I'm all ears.

---

### Post by marcussive on 2011-03-25
oldFred: Thanks, but this is not the issue I'm having. I had 10.10 running two days ago (albeit with my useless Nvidia card draining my battery). Since then, I've deleted some important Win 7 boot partition and now, when running linux from USB or CD, can't get past the try/install menu.
From what I read, linux uses windows to launch or boot? And now that the partition is gone, it can't. I'm sorry, I don't understand this low level stuff.

---

### Post by wilee-nilee on 2011-03-25
> **marcussive said:**
> oldFred: Thanks, but this is not the issue I'm having. I had 10.10 running two days ago (albeit with my useless Nvidia card draining my battery). Since then, I've deleted some important Win 7 boot partition and now, when running linux from USB or CD, can't get past the try/install menu.
From what I read, linux uses windows to launch or boot? And now that the partition is gone, it can't. I'm sorry, I don't understand this low level stuff.

You had 10.10 working becasue the drivers ethier generic or installed were working.

Boot the thumb immediately hit the shift key, for the first larger boot choice menu, hit f6 choose nomodeset boot in.

---

### Post by blind2314 on 2011-03-25
> **marcussive said:**
> blind: maybe you are blind? I repeat: I CANNOT boot linux from USB key or Live CD. I see the options to try, install, etc. but I CANNOT get past this menu.
If anyone knows of ANOTHER way to install linux, I'm all ears.
 
 
Fantastic way to get help; I'll remember this in the future.

---

### Post by blind2314 on 2011-03-25
> **marcussive said:**
> From what I read, linux uses windows to launch or boot? And now that the partition is gone, it can't. I'm sorry, I don't understand this low level stuff.
 
 
No, no it doesn't.

---

### Post by marcussive on 2011-03-26
Apologies, blind. I'm just frustrated.
I'm still going through the material oldFred posted. And putting ubuntu on a USB to try F6 nomodeset and other options (as I can't get to the launch screen at all from a live CD).

Can anyone validate blind's contention: that ubuntu does not rely on any windows boot files? If that's the case (again, I apologize for my lack of low-level computer knowledge), why do I need any of the NTFS partitions that came with the laptop? Can't I just nuke everything and start with ubuntu from scratch?

---

### Post by oldfred on 2011-03-26
If you install wubi, it uses the windows boot loader to launch and is a file inside the NTFS partition. But then it does not use any windows drivers.

Ubuntu does not use any files from windows in a dual boot install. For some hardware there is ndiswrapper that does something to make a windows driver work (usually wireless), but I know very little. But even then you download versions to work with Ubuntu.

Many users completely delete windows. A few come back later and have one applications they cannot live without and reinstall windows. The biggest issue is hardware compatibility and the very newest systems may have hardware that is not fully supported yet.

See threads on SandyBridge & Phoronix comments for example. Only 11.04 works or some drivers may have to be manually compiled.
[http://www.phoronix.com/scan.php?page=article&item=intel_i32100_graphics&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i32100_graphics&num=1)

---

### Post by blind2314 on 2011-03-26
> **marcussive said:**
> Apologies, blind. I'm just frustrated.
I'm still going through the material oldFred posted. And putting ubuntu on a USB to try F6 nomodeset and other options (as I can't get to the launch screen at all from a live CD).

Can anyone validate blind's contention: that ubuntu does not rely on any windows boot files? If that's the case (again, I apologize for my lack of low-level computer knowledge), why do I need any of the NTFS partitions that came with the laptop? Can't I just nuke everything and start with ubuntu from scratch?


It happens, just relax :)

You don't need any of the NTFS partitions that your computer came with, you can "nuke" all of them and start over, installing only Ubuntu onto your machine. If for some reason you still don't trust believe me, the post above me "validates" what I've said (although I assure you I'm not misleading you). If you decide to go this route, we'll help how we can.

---

### Post by marcussive on 2011-03-28
So none of the boot params (nomodeset, removing quiet splash, etc.) worked for me but after some more reading **I found wubi**. I was able to boot windows7 after sort of repairing it with a friend's windows professional rescue disk and then was able to install ubuntu via wubi. Then, I was able to boot ubuntu, create an installer usb and install ubuntu for real (I wiped windows completely--good riddance).

Thanks to all for your help!

---

### Post by Dutch70 on 2011-03-28
:lolflag: ...Nice work!!!

---

