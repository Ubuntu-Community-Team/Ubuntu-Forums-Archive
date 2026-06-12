---
title: "Will not load OS - Flashing White Striped Screen"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by Wrathe on 2009-10-14
This is really wierd.

GRUB loaded up and I booted  Ubuntu 9.04 (I have a dual boot with Vista).  The Ubuntu icon and the loading bar comes up and gets about one third done.  The screen then went into large different coloured pixels (flashing I believe).  I manually reset it and tryed again.
For the second time, the screen suddenly went white (with skinny black vertical stripes) at about one third loaded.  It then kept flashing between a black background and the white one with stripes.  Not keys/mouse worked.  I had to manually reset it.
I did it a third time and it was the flashing white stripped background with vertical stripes and black background again.  I saw no errors or anything.
Now I am in Vista.

This is very odd.

The last time I was on Ubuntu yesterday nothing odd happened.  I was surfing the net and the laptop ran out of battery and shutdown.
Then I decided to go into Vista with AC plug connected.  I just surfed the net, MSN, music, the usual.  The only thing that was different was that I used Vista Business' Complete PC Backup.  It backed up onto my external HDD.  Then more of the usual stuff.  Turned off the computer last night and now 18 hours later......

Maybe by the laptop running out of battery Ubuntu was hibernated? (Don't think so??) Or the Complete PC Backup did something?

Hope someone can help me! Never experienced this before.
Thanks.

---

### Post by Mark Phelps on 2009-10-14
From my experience, the Complete PC Backup in Vista business backs up the Vista partition by default, and any others you select. If you did the backup before you installed Ubuntu, a restore will effectively wipe the GRUB entry from the MBR and you'd only be able to boot into Vista after that.

Is that what you're seeing?

Or did you do the backup AFTER installing Ubuntu, and have since done a restore of Vista, and now, when you select Ubuntu from the GRUB menu, it doesn't load to a desktop?

And, when you say dual-boot, do you mean separate partitions? OR do you mean the side-by-side option of Wubi in which Ubuntu is installed INSIDE Windows?

---

### Post by LewRockwell on 2009-10-14
> **Wrathe said:**
> This is really wierd.not really...

**this:> **Wrathe said:**
> [B]I was surfing the net and the laptop ran out of battery and shutdown.**caused ubuntu to shutdown uncleanly...[/B]

.

---

### Post by Wrathe on 2009-10-15
Wierd for me, cause it hasn't happened to me before.  xD

> om my experience, the Complete PC Backup in Vista business backs up the Vista partition by default, and any others you select. If you did the backup before you installed Ubuntu, a restore will effectively wipe the GRUB entry from the MBR and you'd only be able to boot into Vista after that.

Is that what you're seeing?

Or did you do the backup AFTER installing Ubuntu, and have since done a restore of Vista, and now, when you select Ubuntu from the GRUB menu, it doesn't load to a desktop?

And, when you say dual-boot, do you mean separate partitions? OR do you mean the side-by-side option of Wubi in which Ubuntu is installed INSIDE Windows?No.  I did not restore Vista.  I backed it up.  Vista said it would not rewrite over my previous backup if I had enough room.  But it did rewrite over the previous backup even though it had 140GB and said it would only take a max of 55GB. -.-

No I am not seeing that.  
Vista came pre-installed then I installed Ubuntu in its own extended partition.
Ubuntu was working fine the day before.

I click on Ubuntu in the GRUB menu and then it comes up with the Ubuntu design (like below).
[IMG]http://www.dsl.sk/images/articles/2007-05-06-ubuntu-1.png[/IMG]

It then changes to one of the following screens:

Here is a shitty drawing in paint of what then happens.

1. First the flashing colours.  I tried booting from Ubuntu again and the flashing colours came up again.  This is what it keeps flashing between.  Note: I don't think the colours were exactly this bright, but you get the idea.  Also all the squares are meant to be the same size.  This flashing colours only happened the first time I did it and when I turned it on today and tried again.  (So only the first time and then the first time again after it had been shutdown for 16 hours or so)
[IMG]http://img63.imageshack.us/img63/5663/flashingcolours.jpg[/IMG]

2. The flashing white background with stripes and black background.  This is what happened the 2nd and third time without it being turned off.
[IMG]http://img124.imageshack.us/img124/5095/flashingwhitewithstripe.jpg[/IMG]

Any ideas?

---

### Post by Bartender on 2009-10-15
Well, I'm not good at fixing Ubuntu, so I know what I'd do if I'd just installed Ubuntu a couple of days ago, then it went haywire.

I'd just re-install Ubuntu.  Good practice.  I've read several posts where people stated that Ubuntu's response to low-battery needs some work.  My understanding is this - Windows knows enuf to stop processes and shut down.  Ubuntu just keeps motoring on until something - HDD motor, RAM, chipset, whatever - quits working.  So my guess is the / partition is corrupted in a way that you or I might find very difficult to fix.  Reinstallation should take less than an hour.  If you're going to format / and leave /home untouched, be sure to use the manual partition option, mount / to the same partition as before, mount /home and swap to the same partitions as before, don't format /home, and use the same username/password as before.

EDIT:  Re: your Nvidia graphics - go into System>Administration>Hardware Drivers and let Ubuntu do a search for proprietary graphics drivers.  Y ou have to be online for this.  If it finds anything tell it to "enable", which actually means "download and install".

---

### Post by Wrathe on 2009-10-15
Ah okay.  Thanks.
Now I know to put in the AC plug before it gets below 3% (I put the plug in at 3% but it must take some time to warm up before it starts taking from the AC plug??).

Was afraid very few people would know how to fix it and there was a low chance of one of them actually posting.  :P


_I am reinstalling Ubuntu._


[SIZE=3]_**TOPIC REMAINS UNSOLVED!**_[/SIZE]

---

### Post by Wrathe on 2009-10-20
Wow.  Happened again. -.-

This time I manually installed my NVIDIA driver (it didn't show up in Admininstrator > Hardware Drivers so downloaded driver, shutdown X etc.) then after I installed it, restarted it etc.

Then I opened up Hardware Drivers and the NVIDIA driver was there saying it was not installed.  I clicked apply.  Big mistake.  The Hardware Drivers window freezes.  Went to appearences and funny enough it let me press 'advanced' or 'expert' or whatever it is called desktop effects.  Installed compiz, played around.  Went to turn it off, but couldn't close Hardware Drivers so clicked logout anyways.  It did the usual logoff thing but before it finished the screen was split in half with a window popped up.  The left side of the screen was really meant to be the right side of the screen and the right side of the screen was meant to be the left side of the screen.  To get to the left side of my screen (really my right side of the screen) I had to move the mouse all the way to the right side of the screen then it would appear on the far side of the screen.  (Hope you get what I mean)  It was saying it could not understand my video card.  It was too low or something.  Clicked cancel cancel blah blah then the screen went a black screen for a couple of minutes.I manually reset it. Went into Ubuntu and the loading bar went all the way across but instead of going to the login screen it goes a flashing white with black stripes and a black screen.

[Sigh]  Corrupted it again. [faint ha]

Lucky all the downloads of the wireless and video drivers and how to install them are in the /home partition.

Guess it will need to be reinstalled, which will be done in the next couple of days.  [sigh]
Third time lucky!

---

### Post by Peter09 on 2009-10-20
Have you tried going into recovery mode and re-initializing your video drivers?

---

### Post by J Caffrey on 2009-10-20
Don't Install the Nividia restricted drivers.I did and got black screen had to reinstall.

---

### Post by spiderbatdad on 2009-10-20
> **Peter09 said:**
> Have you tried going into recovery mode and re-initializing your video drivers?

Exactly, boot into recovery and enter: ```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Wrathe on 2009-10-21
That worked.  It got my desktop etc. working again.  Thanks!

Logged on then tried to update graphics driver (System > Admin > Hardware Drivers).  It detected the driver. Then enabled the driver (didn't freeze this time). Checked if driver worked (only way I know how is System > Preferences > Appearences > Visual Effects) and it didn't work.  Logged out and then it was a black screen.  After a couple of minutes it automatically reset (wasn't me).  Tried to 'auto repair graphics driver' and funnily enough it does the same thing your command does.

Anyone know how to install a NVIDIA G102M Cuda driver?
I wrote out what I did last time and is as follows:

>   
 Download NVIDIA-Linux-x86-185.18.36-pkg2.run (x86_64 for AMD64) from [[COLOR=#000080]_www.nvidia.com_[/COLOR]]("http://www.nvidia.com/") to desktop.
 

 You must close X (the Graphical User Interface aka GUI).  Open terminal and type:  
  
 sudo  /etc/init.d/gdm stop
  
 Press Ctrl + Alt + F1 (or F2 - F6) to open a different desk.  Login with your username and password.  Now type: 
  
 cd Desktop 
 sudo sh NVIDIA [press Tab] 
  
 Now go through the NVIDIA installer.


At the moment Ubuntu detects that the computer has a driver, however, when you press enable it stuffs it up.  Should I just do what I did before and NOT TOUCH it in Hardware Drivers?

---

### Post by biscoito1r on 2009-11-05
I'm having similar problems, I tryed to use the "dpkg-reconfigure -phigh xserver-xorg" command with no success. I'm running Ubuntu 9.04 on its own, and I have a ATI card. Is there a way to deactivate the card and run the open source one ?

---

### Post by biscoito1r on 2009-11-05
I removed the restricted drive with the command and it worked
sudo apt-get remove xorg-driver-fglrx

---

