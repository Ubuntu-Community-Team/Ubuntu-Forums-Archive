---
title: "Too Tiny VirtualBox"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Hastor on 2010-05-13
I've been off ubuntu for awhile since I was warned against some semi-fictional myths about its affects on computer stability. Anyway, I recently found a way around this by using the virtualbox software and creating a virtual machine capable of running a risk-free ubuntu. he problem I'm having is that the window my OS always appears in is so small that, aside from looking nice, Ubuntu is effectively useless. Whenever I try to expand the window there is a huge gray space left and the OS remains the same size. I've tried going into the OS and expanding it, going through virtualbox forums, and using the guide for virtualbox, but in all cases I was met with little to no answer. I would really appreciate any help in the matter. Thank you.

---

### Post by Sef on 2010-05-14
Moved to ABT.

---

### Post by Paqman on 2010-05-14
You'll need to install the Virtualbox Guest Additions to get a decent screen resolution on your VM.

I'm intrigued to hear what people were telling you about Ubuntu being "unstable". Because:[LIST=1]
[*]That's just plain wrong.
[*]There's no way Ubuntu can adversely affect the stability of other OSes on your machine.
[/LIST]

---

### Post by Hastor on 2010-05-14
How would I go about getting these guest additions?

About the instability, I have a friend who works at a pretty well run firm and his IT guy told him that running Ubuntu as one of the main operating systems for a computer could adversely affect other operating systems. He said that the risks could include the complete erasure of windows 7 (my current OS.

Thank you very much for your response.

---

### Post by themusicalduck on 2010-05-14
Go to devices and then click Install guest additions.

Hopefully this will automount a CD to install them from. If it doesn't run automatically, then you can press alt+f2, and enter ```
gksu nautilus
``` then navigate to the guest additions drive which should be listed on the left.

There should be a file called VBoxLinuxAdditions-x86.run, double click it and say to run in a terminal.

As to instability, it is true that Ubuntu can be used to delete another operating system, but only if you tell it to. If you do some research into it then it isn't too hard. A guide on installing and using Ubuntu is here - [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Should always do a backup if you did decide to install it though, and also defrag Windows beforehand if you're going to do repartitioning.

---

### Post by tmx84 on 2010-05-14
On Virtual Box go to Devices>Install Guest Additions, this will mount guest additions on your desktop.  From there, Open that, and there will be some install files, you can either run it from terminal or just install it... If you need a better explanation just google it.. there are plenty of tutorials around to install guest additions.. I'm just going off memory..

---

### Post by Hastor on 2010-05-14
Everything worked out beautifully. Thank you very much for your help.

---

### Post by Hastor on 2010-05-17
After using VB for a while I seem to have hit a dilemma. I have steadily grown to love Ubuntu's fluidity and functionality and I am seriously considering installing it as my only OS. The only thing that stops me from doing this is the nagging thought of Ubuntu's structure. Though I am near certain that what I was informed of earlier was a nice ways off from the truth, I still worry that Ubuntu might not be stable enough for a stand alone OS. Because of this I end up caught between the somewhat "scaled-down" feel of virtualbox and my uneasy thoughts about Ubuntu's stability. I would love to just go ahead and make it my primary OS, but I just don't have enough experience in the field to risk a 1000$ computer on a whim. Any help would be much appreciated. Thank you.

---

### Post by 3rdalbum on 2010-05-17
Ubuntu is not a fly-by-night distribution. It's been around since 2004, and it's an enterprise-level distribution; big corporations and nonprofits use Ubuntu on their systems.

Linux itself has been around since 1991, with backing from big companies such as IBM, Sun Microsystems (now Oracle), Red Hat, Novell and others.

Ubuntu is certainly stable enough to use as your everyday operating system, and it has been for years now. Ubuntu won't damage any other operating systems that you use, it won't even touch them unless you explicitly tell it to. Just make sure that you use the "Resize a partition" option in the installer rather than "Erase whole disk", but you'd know that. Then whenever you boot up you'll have the option of booting into Windows or Linux.

However, Windows isn't as nice. If you install or reinstall Windows, it will overwrite Ubuntu's bootloader with its own, and you lose the ability to boot into Ubuntu until you reinstall Ubuntu's bootloader.

I run Ubuntu single-boot on three computers, one of which stays turned on 24/7; and on another computer as part of a dual-boot.

---

### Post by Lucky. on 2010-05-17
Hi Hastor!

After toying with virtualized Ubuntu for a few years, I finally made the 100% switch and had Ubuntu running on my computer.

I can definitely vouch that it's extremely stable, but in some cases certain hardware won't work...which gives the appearance that it's not stable when you first start out.  Some computers and hardware just work great - but for others you can spend hours and days trying to get hard drive RAIDs working, sound cards, video cards, network cards, wireless cards, etc.  It's very frustrating, but if things work out for you (or you are able to fix any problems that arise), it's a breeze from there.  And these problem are definitely less likely to happen than they were years ago.

Other transition issues arise from finding software that you may have gotten used to in Windows.  No more Internet Explorer, no more Photoshop, etc. unless you do tons of tweaking and playing with WINE or something else.  In order to ease this transition, I suggest trying open source software in Windows for a few months before you switch.  For example, try using Firefox, Gimp, OpenOffice, VLC, GnuCash, etc if you haven't already used them.  That way if/when you move to Ubuntu, it's less of an immersion shock when you move over.

Of course if you have a Windows disk, you can always use VirtualBox in Ubuntu to create a Windows VM to run that special software you need.

As long as you know how to make backups and reformat your computer with Windows (or use a restore CD/DVD to bring it back to stock settings), there's no risk at all to try Ubuntu - you can always go back if you don't like!  Or you can set up Ubuntu to dual-boot with Windows.  I get frustrated with dual-booting, but a lot of people like it a lot.

Good luck!

---

### Post by consindo on 2010-05-17
Hi! I've used Ubuntu 100% for about one and a half years now. If you really need some Windows App for your iPod or something, you can always dual-boot or put Windows in a virtual box

---

### Post by lukeiamyourfather on 2010-05-17
I don't know who told you "Ubuntu affects computer stability"  (assuming they mean negatively) but you should disregard anything they ever say again about computers and technology. :roll:

---

