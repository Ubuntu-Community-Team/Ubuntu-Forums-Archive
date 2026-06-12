---
title: "boot stops at grub&gt;"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by blindape on 2009-08-25
Hi, I have had Ubuntu 8.10 installed on a windows vista computer using wubi since February.  I have had now problems with the install and have been able to use for business and personal use until this morning.
Last night I put the computer to sleep/suspend and when I went to 'wake' it up this morning the computer froze and I had to turn it off with the power button.  when I went to restart the computer after this I got to the OS choice menu and chose Ubuntu and then got to a screen with the following.

[Minimal BASH-like line editing is supported...etc.]
grub>

there weren't alot of commands available and when I pressed esc i got the following menu.

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
commandline
reboot
halt

when I select the top item it brings me back to this same menu, when I press any of the other options down to command line I get the [Minimal BASH-like line editing is supported...etc.] message again.

If I choose the windows installation everything boots up fine. hence here I am typing in this distress call.

I have found menu.lst but in a different location from the ones listed above (d:\ubuntu\winboot)

Other things I have looked at have suggested running chkdsk on the drive that ubuntu is installed on (in this case it is the d: drive).  I have done this but still get the same result when I try to reboot.

Other posts have talked about re-installing ubuntu, however while the majority of my work is backed up there are some files that I do need to access to finish the job that I am currently working on before I could re-install ubuntu.

any help is really appreciated as I'm starting to freak out a little as my work has come to a screeching halt until things are back up and running.

Regards,

John Curwood

---

### Post by lawrence1l on 2009-08-25
Hi John!

This sounds a bit like what I have seen with my Mepis dual boot system.  It will, at long last get to a prompt, after listing numerous errors.  I can log in as 'user' or 'root' and tell it to start the GUI, because it won't on it's own, but it doesn't work.  The 'startx' goes nowhere.  Fortunately, I have nothing serious going on there.  I use the linux side of the drive strictly to encourage the kids to use it to surf, and reduce the potential of them picking up a bug of some sort.  

As with your experience, the selection of the 'Windows' choice in the boot menu works just fine.  I wish could offer more than sympathy.  I tried repairing the MBR, but it didn't do any good.  Being a rookie, I have little to offer, other than to re-install.  It does occur to me you may be able to finish your project using the 'live CD', then do the re-install afterward.  
Regards,

Larry

---

### Post by matthewbpt on 2009-08-25
Wubi installs are much more suceptible to data corruption, and one forced shutdown can cause the virtual disk to corrupt so it wont boot anymore. If you run a chdsk windows will find corrupt files and possibly fix them, but it wont move them back to its original location. What I had to do once with a friends wubi install that got corrupted, after running a check disk I had to find a hidden folder in the drive i ran the checkdisk on, called 'found.000' and in there were some essential files needed in the c:\ubuntu folder, so I moved them back to the right place and then wubi worked again. I'm not sure now exactly what files they were and what folder inside d:\ubuntu they needed to be in, but hopefully this will guide you in the right direction. I recommend though that once you've recovered the wubi install, you back up everything in it and then do a proper ubuntu install onto a partition in your hard drive, this will cause much less headaches and will be faster as well.

Matt

---

### Post by matchstich on 2009-08-25
i do not dual boot ,  but had problems with grub and error 15

found some threads that might help you

[http://ubuntuforums.org/showthread.php?t=224351&highlight=defrag](http://ubuntuforums.org/showthread.php?t=224351&highlight=defrag)

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

[http://members.iinet.net.au/~herman546/p15.html#How_to_get_GRUBs_Command_Line_to_investigate_a_computer](http://members.iinet.net.au/~herman546/p15.html#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)

there are links in both that point to other solutions.

thanks

---

### Post by blindape on 2009-08-25
Thanks for your replies guys.  I have found the files in the hidden found.000 folder and put them back in their rightful place.  Ubuntu boots fine again now. I admit I am reluctant to do a full ubuntu install as this is the first problem after six months of working well. and my hard-drives are pretty small and I don't have a lot of spare room for creating an extra ubuntu partition.
by the way Matt how much faster would it go on a proper install as ubuntu-wubi already goes like a rocket compared to vista.  I did try doing a proper install onto an external HD but the computer just doesn't seem to want to boot to it.  It will boot to a 'live' ubuntu usb stick however, just not the external HD.

Cheers,

John

---

### Post by serialtoon on 2009-08-26
This may not be the best of help, but have you tried using Super Grub? Fixed most of my issues with installation.

---

### Post by matchstich on 2009-08-26
thanks for the info on super grub.  went and ordered a copy from osdisc.com

---

### Post by LewRockwell on 2009-08-26
> **serialtoon said:**
> This may not be the best of help, but have you tried using Super Grub? Fixed most of my issues with installation.

so you are stating that Super Grub Disk works with a WUBI installation?

.

---

### Post by matchstich on 2009-08-27
lew rockwell    hope you do not mind , but, i ripped off the part of your signature about marking post's as solved, and put it in my signature.

---

### Post by sirishy2k on 2009-10-04
how to find found.000 folder
my wubi installation is in d:\ubuntu

---

