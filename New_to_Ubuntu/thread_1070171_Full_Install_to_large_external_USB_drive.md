---
title: "Full Install to large external USB drive"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Amenhoteph on 2009-02-14
Okay, after three days of searching through forums for answers to my questions I have decided to post the questions.

I bought my first Vista machine 3 days ago, 2.9 days ago I decided to re-familiarize myself with Linux.  I am not going to be able to escape the Windows environment for my work related applications, but I would really like to for all my personal activities.  I travel a lot and it would be very nice to be able to carry one laptop instead of a work machine and an personal machine, especially given the joys of air travel in the US.

I have an 8Gig USB key that I have installed a couple of flavors of Linux on.  The set-up works great for all three of the laptops that are sitting on my desk now, but I need a little more juice than the 8Gig'er and a [www.pendrivelinux.com](www.pendrivelinux.com) OS version has to offer.  Which brings me here.

What I would like to do is a full install of Ubuntu to an external 320Gig Western Digital, or similar drive, so that I have a persistent OS.  I would like to be able to plug the drive into my windows machine, like the pendrive version, reboot and suddenly the work laptop becomes my personal laptop.

**Question one:** Is this even possible with a "non-pendrive" form of Ubuntu?

**Question two:** Would the process be just downloading the 8.10 iso, formatting the external to FAT32, running the partion/install on the external drive and setting up my BIOS to boot from USB Hard Drive?  I don't want to have to set up Grub or anything on the work computers, for obvious reasons.

**Question three:** If both of the above answers are "yes" then what potential issues can I expect when I move the drive from laptop to laptop with respect to things like wireless drivers and such?(which are the only thing that seem to be giving me problems with the pen drive version)

Any and all help is appreciated more than you know.

---

### Post by gn2 on 2009-02-14
Mechanical USB drives are not good as bootable devices as they do not always spin up in time to be recognised by the BIOS during boot.

I would suggest installing to the flash drive and using a 2.5" external drive for file storage if required.

Alternatively get a 2.5" enclosure and put an SSD in it.

Or create a dual boot on the internal drive and use a USB hard drive for file storage.

The "Pendrivelinux" persistent live installs are the best bet for use on multiple PCs and laptops, saves problems with drivers and hardware being different on the various machines.

---

### Post by Kain000 on 2009-02-14
Yes and yes


You just need a live cd or your usb drive to load up your live session, and install to your large usb drive.

when you want to boot into your ubuntu laptop just select a one time boot option or go into your BIOS and change the first boot device to the USB disk and you should be fine.


You could also just use a virtural machine inside windows, or visa-versa windows inside linux.

---

### Post by adult swim on 2009-02-14
if you are going to install to your usb drive, DONT FORGET TO INSTALL GRUB TO THE USB DRIVE.  if you do a normal install and install ubuntu to the external drive, it will install grub to your computers internal drive.  if you boot a machine without the external plugged in, you will get a grub error.  check out post 5 here
[http://ubuntuforums.org/showthread.php?t=1042219](http://ubuntuforums.org/showthread.php?t=1042219)

---

### Post by Amenhoteph on 2009-02-15
Okay, first off that guide you pointed me to worked great.  I installed everything to the external and managed to to do any damage to my existing Windows system.  I rebooted the machine with and without the external drive and it worked just like I hoped that it would.

I moved the drive to a second laptop, Sony Vaio PCG-6P2L, only to  discover that the version of PhoenixBIOS running there (r0030j4) does not allow for boot from USB drive, only USB Flash.  Will deal with that later I guess.

Then I moved to the new Vista machine, a Gateway MD7181u, which does have the boot from USB Drive option.  Grub loads and the Ubuntu splash loads up.  Then something odd happens.  The LCD cycles up and down in brightness, with nothing displayed.  After a couple of minutes I get this:

```
* Starting System Tools Backends systems-tools-backends     [ OK ]
* Starting anac(h)ronistic cron anacron     [ OK ]
* Starting deferred execution scheduler atd     [ OK ]
* Starting periodic command scheduler crond     [ OK ]
* Enabling additional executable binary formats binfmt-support     [ OK ]
* Checking battery state. . .
```

And that is where it hangs.  There is a blinking cursor and that is it.

I tapped the power button and something to the effect of "* Stopping Gnome display manager" flashed up and then the power went off.

I am not sure if it is worth noting, but I am able to boot this machine using #!CrunchBang Linux off of a USB key.

Thoughts?

---

### Post by Amenhoteph on 2009-02-15
Okay, colour me confused.  I rebooted the machine a couple of times to try and catch any messaging that may have slipped passed me and the darn thing booted up full and loaded.  I am posting this from the machine that would not get past the battery check and it is currently downloading and installing 253 updates.  Hopefully one of them will fix the wireless problem (still not finding the card) and I can move on to the next stage.

Again, thanks Adult Swim for your directions.  I am sure that I would have borked up one of my windows machines had you not given me the heads up on the Grub install location.

---

### Post by adult swim on 2009-02-15
i have an install on an external drive that i have been lucky with things working on different computers.  probably the biggest problems you will have, as you have already found, will be getting the wireless and video working on different machines.  to try and get your video working you can try to run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and see if you have any luck with that.  as far as wireless goes, it just depends on the cards that the computers you will be using have.  my computer uses is broadcom which uses b43  i had to set up manually and the other computers ive tried with have intel cards that work automatically.  you can find your devices by running ```
lspci
``` from a terminal and a quick google will usually point you in the right direction.  the problem with a whole install that you move around is you may find yourself configuring alot if the computers you are using it with vary.

---

### Post by Amenhoteph on 2009-02-15
After all the updates installed I clicked the network icon and behold: Wireless Networks!

I didn't even have to reboot!  This is great.  Even if I have to do some reconfiguring here and there for different machines, at least I will be getting some enjoyment from it, rather than swearing at a Vista control panel.

Thanks again!

How do I mark this as Solved, or do I need to?

---

### Post by Amenhoteph on 2009-02-25
Just a follow-up post on this topic with something to watch for when using one of these.

My external install is doing just what I imagined it would.  I have not had this much fun with a piece of hardware since I got a tape drive for my TRS-80.  I did have one glitch, so I thought it best to share.

I am switching between three different laptops and one desktop.  After booting up a Dell Latitude and then returning to my main Gateway laptop I lost the ability to enable Normal or Extra in the Visual Effects.  As it turns out, the driver for video card just got disabled.

FIX: System > Administration > Hardware Drivers > Activate - ATI/AMD proprietary FGLRX graphics driver

Reboot and problem solved.

---

### Post by haiku88 on 2009-02-25
there are a few good pages on this that Google will find, I followed one with suceess for a USB hard drive install...the key was that the author said to disconnect the internal hard drive so there was no chance of the boot record being changed on it,I removed the HD from my laptop...I also had to change the boot order on my bios but that was easy.
the page I used is at [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/#more-372](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/#more-372)

---

### Post by sgosnell on 2009-02-25
Yeah, switching between that many different machines will require some reconfiguring as you switch.  It should be doable, though, if you're willing to do the work.  You'll probably find that you may have to install new drivers if you boot from different machines, but it should eventually work on anything.

---

