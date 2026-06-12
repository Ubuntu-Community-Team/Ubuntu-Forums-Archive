---
title: "DVDrw drive doesn't show... can I burn .iso using LiveCD?"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by jage on 2010-01-27
Unfortunately googling LiveCD and CDrom turns up a lot of information about running ubuntu from a USB stick, and other information that seems irrelevant to my issue.

The first problem is that using LiveCD the cdrom (actually a DVD burner) doesn't show up in File Browser.  There is no /dev/fd0 and I tried:

sudo mount /media/cdrom0/ -o unhide

in the "Run Application" window, which spun the drive but did nothing in the GUI.

I also cannot eject the LiveCD disk using the button on the tray.

I have no idea what to do (and don't take the things I've tried as reflecting any understanding of the problem).  My Hardware Drivers window on has the Broadcom B43 wireless.

I'm running LiveCD on a machine with a failing HD and was going to burn some other Ubuntu's to play with while I wait on UPS.

/media has only the mounted partition of the failing HD and both partitions and the external USB drive show up in places, and "Computer" along with filesystem, but no CDrom drive.

---

### Post by J V on 2010-01-27
there isn't supposed to be, while running live disc the drive is occupied... the whole time...

If you stick a new disc in to burn the burning software is going to come from where exactly?

---

### Post by Hospadar on 2010-01-27
what is it that you are trying to do? burn a cd while running linux from the livecd?  If you only have one drive that's pretty much impossible since the system needs the data on the livecd to run.

Why would you need to do this, does the system not have an OS on it right now? if so, why not just install ubuntu and burn the cd?  If it's windows you can use a program like infrarecorder to burn images.

Alternatively, you can make a usb boot stick and boot off that, then you can use the disk drive to burn stuff.

---

### Post by jacklinux on 2010-01-27
Wouldn't it be possible for him/her to boot up ubuntu via USB and then burn an .iso?

---

### Post by J V on 2010-01-27
sure... he has to DL the iso from the live disc, use unetbootin... oh ****, can you install on a live disc? if you can't you're really not gonna get it... but if you can, install unetbootin, boot from that, and burn baby burn!

---

### Post by jage on 2010-01-27
I kind of suspected that might be the case (the drive is necessary for LiveCD).

The HD is partitioned but has many bad sectors.  There is no reason not to install ubuntu but I'd hoped to spend my time running lucid from LiveCD (I'm using karmic now) and trying the Jaunty studio version to try to decide which to install.

[QUOTE="JV"]If you stick a new disc in to burn the burning software is going to come from where exactly?[/QUOTE]

By Just typing "sudo apt-get install *whatever*"... how the hell I'm suposed to know what *whatever* is I don't know.  I kind of came into this thinking Brasero might be the burning software since it has a burning CD icon, but finding the cdrom drive seemed a little more pertinent.

I like Ubuntu, but I *know* that if I install XP back on my failing drive that I'll have CD burning software and the right drivers, which worked 5 years ago and should work just the same.  Is it worth the pain of an XP install to avoid coming back here and asking where I get the burning software and probably where I get drivers?  Probably, but then if I'm going slinking back to XP, I don't need to burn some other Ubuntu flavors to try.

---

### Post by J V on 2010-01-27
*sigh* this will take a while...

The point is that the software to install/burn/whatever is on the cd, if you remove the cd to get one for burning then suddenly the burning software is gone... you need to make a live usb

---

