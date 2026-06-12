---
title: "dual boot, no grub menu. Is this possible, and if so, how?"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by wep940 on 2011-01-22
I, like many of us over the years, have been doing remote support for my elderly parents who live about 1800 miles away.  I've never used remote desktop, etc., just walked them through things hours at a time on the phone.  Well, they got another virus (they use Windows) and now they don't want me to fix it and they don't want to get on the net because they don't know what the virus does.
 
So, I have an older Gateway laptop I want to send them.  Right now I have Windows and all the programs they use installed.  I know they would prefer Windows and also know they just don't have the "oomph" anymore to switch operating systems all together.  So, what I'd like to do, if even possible, is this:  load Ubuntu to the hard disk as well, like a dual-boot system, but with no grub menu.  I want there to be no change in how they would normally do things.  But, I'd like them to be able to get on the net without the worry of virus or malware infection, hence the installation of Ubuntu.  So, is there a way to do this, then have like a boot diskette that would boot up the Ubuntu installation?  What I'd like to be able to tell them is that when they want to get on the net, put this floppy in and reboot.  I know this sounds similar to the LiveCD, but believe me, they don't have the patience to wait for that to boot on that old laptop.  Plus I need to install wireless drivers.  I thought about some type of USB installation (I don't know the terminology - but something that runs as a live, updatable system, not as a LiveCD clone).  HOwever, I don't seem to be able to boot the laptop from USB. 
 
If anyone could help out on both of those ideas it would be greatly appreciated!

---

### Post by ExileAmongYou on 2011-01-22
Well to boot the laptop from the USB, you usually have to go into your BIOS settings, generally by pressing F10 or F12 on the very first screen you see when you turn the laptop on. It should say "Press F10 to enter setup" or something. Once you're into the BIOS settings, you need to track down the "boot order" option and move "USB hard-drive" to the top of the list, so that it boots first.

---

### Post by wep940 on 2011-01-22
Well, you see the laptop is old enough there is no boot from USB option in the BIOS, and it's running the latest BIOS.  Hence why I was thinking a boot diskette.
 
Here's what I was thinking, but I don't know if it will work:
 
- install Ubuntu for dual boot
- via grub menu, boot Ubuntu
- create Ubuntu boot diskette
- via Windows repair console reset the MBR so it is Windows only, no grub
 
I was hoping that this would create a boot diskette to boot the current Ubuntu, with the end result being that by default there is no change to the PC for booting Windows, but using the diskette to boot Ubuntu to run from the hard drive.

---

### Post by drs305 on 2011-01-22
You could just install Ubuntu on the disk, use Grub 2, have it boot directly to Windows with no display of the menu. By using a custom menu to boot you could assure that the menu didn't change.

If something should happen and they needed Ubuntu, at that time you could tell them to hold down the SHIFT key and a menu would appear and they could select that other (Ubuntu) OS.

You could have Ubuntu set up so it opened Firefox by default so they would be able to just start browsing (if you can get the Internet connection set up).

---

### Post by wep940 on 2011-01-22
I'll give that a try - it may take me a while.  I'll probably post back with a question or 2 as well.  I'm thinking that if I can make Windows the default, that then I'll probably just let grub handle the booting.  One thing I don't know for sure is how to get Firefox to start on boot - I assume it either goes in the default users' startup file or something similar, but I don't know what that is called.
 
Thanks!

---

### Post by drs305 on 2011-01-22
> **wep940 said:**
> I'll give that a try - it may take me a while.  I'll probably post back with a question or 2 as well.  I'm thinking that if I can make Windows the default, that then I'll probably just let grub handle the booting.  One thing I don't know for sure is how to get Firefox to start on boot - I assume it either goes in the default users' startup file or something similar, but I don't know what that is called.
 
Thanks!

For startup apps, just put them in System, Preferences, Startup Applications.

As for getting Grub2 set up, take a look at the links in my signature line. Some are pretty involved but the "Tasks" link may be all you need to set the defaults; "Basics" provides a bit more detail. 

To get the custom menu set up, once you have the system configured the way you want, just post your /boot/grub/grub.cfg file contents and we can easily build one for you.

---

### Post by wyrless2002 on 2011-01-22
> Plus I need to install wireless drivers. I thought about some type of USB installation (I don't know the terminology - but something that runs as a live, updatable system, not as a LiveCD clone).

Unfortunately, I think that [WebConverger]("http://webconverger.com/") falls under the category of a LiveCD clone, but, this is the first thing that came to mind when reading your initial post. I don't recall what the boot time was from a cd, I only use it now from Virtualbox, but I know it only loads the minimum of dependencies to run the browser. This may actually work to your disadvantage if it doesn't have the wireless drivers that you need. You may also note that they advertise services for customization of the browser (Basic price: 100GBP,~115EUR/~150USD). So you could have it open the local newspaper website, online banking, email, and your family flickr page on boot, so there is less confusion as to what web addresses to go to. I'm Sorry if this doesn't help, I figured it couldn't hurt to put it in front of you. I have a similar but more local situation, so, I'll be interested in reading any further developments.

-Best Wishes
Aaron

---

### Post by -kg- on 2011-01-22
You know, you can also set the "Timeout" value in GRUB to a very low setting.

I would install normal dual boot, with GRUB in the MBR and Windows set as the default OS.  Then set the Timeout value to a low number.  Zero wouldn't display the GRUB menu at all, but boot through directly to the default OS.  I'd opt for a low value though, like 1 second.  That would flash the GRUB menu for a second, then boot through to the default OS after a one second delay, giving you a very short time to catch GRUB and select Ubuntu, if desired.

I'm not sure where a tutorial on GRUB2 settings would be, but they're all over the web and quite searchable.  I'm sure someone here will supply a link, should you decide this is what you want to do.

<Edit> And as usual, I should read previous posts more thoroughly.  Already been basically suggested by drs305 above.  #-o

---

### Post by wep940 on 2011-01-23
Well, seems I have a problem to overcome before I can get to grub anyway.  I tried the 10.10 LiveCD but the video disapeared right after a very quick flash of the Ubuntu screen with the 5 dots, at which time nothing worked.  So I tried 10.04 - got further, but don't get the GUI.  I got to the purple screen, then it disapeared.  Could get in a terminal 0.  Tried startx - said it was already running.  Tried stopx - said not a valid command so I guess I don't know how to stopx (unless it's supposed to be gdm -stop, but I didn't think gdm was up at this point).  Tried dpkg --configure xorg, but said it was already configured.  A shutdown -r now result in the sys message being sent about the system going down, but it never rebooted.
 
This is an old laptop - PIII 1ghz, plenty of memory (636meg), but it does have an old Intel 82830 graphics chip.
 
So, right now I'm kind of stuck - I don't know how to get passed these problems.  Whenever I've used the LiveCD it's always been on my desktop and everything has always gone great.

---

### Post by wep940 on 2011-01-23
I'm downloading the alternate disk right now.  I figure since I can get to terminal ok, it's just a driver thing with X.  So, I'm going to install from the alternate disk, then boot via grub and edit the boot line to include nomodeset.  After it's up I'll then update the grub file so it has nomodeset then update-grub again.
 
If I don't want the Ubuntu to do updates, is there a way to turn-off updates?  I'd like to keep it as I delivered it - this also allows me to edit the grub file I shouldn't so that the titles are Windows and Get On The Interent only.  A little away from what I should be doing, but I want to keep it simple for my parents.

---

### Post by wep940 on 2011-01-23
Okay, got everything working by using the alternate CD and then speficying nomodeset on the boot line.  I also edited the grub.cfg file to customize it for my parents (I know I'm not supposed to edit it but instead edit the various grub2 config files, but this was the easiest for me).  Now my parents will get a menu at boot that says:
 
Get On The Internet
Windows XP Professional
 
With XP being the default.  I removed everything for the recovery console and for memtest.  
 
In addition, I put firefox &u in a new startup entry.
 
 
The result is that by default Windows will come up just like they are used to.  When they want to get online, they just reboot and select "Get On The Internet" and Ubuntu boots, enter in the user/password and then the Firefox screen comes up.
 
This is going to work great for them as they need things simple.
 
Thanks to everyone for your help on this!

---

