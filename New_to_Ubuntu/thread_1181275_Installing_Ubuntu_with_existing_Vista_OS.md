---
title: "Installing Ubuntu with existing Vista OS"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by copan on 2009-06-07
Hello all,

I am very new to Linux OS's, but I have installed them before.  This time, however, I'd like to ask you for a tutorial or instructions because I am doing it a little differently this time.

Sorry if this question has already been asked, I did search though.

Anyway - I am installing Ubuntu from USB 1GB flash drive, and I currently wish to keep my windows OS active.  How do I, or is it possible, to partition the drive and keep windows there while installing Ubuntu.. I believe I have done this before but I don't want to go through the same trouble.

Also, what do I need to do to boot from USB - just go into BIOS?

Thank you!

---

### Post by Therion on 2009-06-07
How to dual boot, with Windows installed first, explained here:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Link goes to Windows XP being installed first, but if you have Vista installed see the sidebar on the right for that specific tutorial.

As for booting from a USB thumb drive, I'd suggest looking into **Unetbootin** to set up your thumb drive.  As for how your particular PC is going to handle booting from USB that's hard to say.  BIOS settings would be the first place to look though.

---

### Post by murray92 on 2009-06-07
Firstly find out whether or not your PC can boot from USB, if not then you will have to use a CD. To do this, press F12 (probably, but might be different on your pc) to open boot options, if there is a USB option then thats fine, otherwise use a CD.

I dual-boot myself, and I used the partition editor in windows to set up a 15GB partition to install ubuntu on. You could use Ubiquity (the default ubuntu installer on your USB drive) but the Vista partition editor is easier to use i find. To use it go to Start, right click 'Computer' and click manage. Go to the partition editor and select what kind of size you want to partition for ubuntu.

When thats done, boot into ubuntu from your USB, and you should have the option to install ubuntu. Answer the easy questions and when you get to partition manager select manual. This brings up a list of your partitions. Select the one you want to install ubuntu on, you should be able to tell which one by the size. And from there on you should just have to wait until its done.

I think ive mentioned everything, but if you have any problems just ask :)

---

### Post by copan on 2009-06-07
> **murray92 said:**
> Firstly find out whether or not your PC can boot from USB, if not then you will have to use a CD. To do this, press F12 (probably, but might be different on your pc) to open boot options, if there is a USB option then thats fine, otherwise use a CD.

I dual-boot myself, and I used the partition editor in windows to set up a 15GB partition to install ubuntu on. You could use Ubiquity (the default ubuntu installer on your USB drive) but the Vista partition editor is easier to use i find. To use it go to Start, right click 'Computer' and click manage. Go to the partition editor and select what kind of size you want to partition for ubuntu.

When thats done, boot into ubuntu from your USB, and you should have the option to install ubuntu. Answer the easy questions and when you get to partition manager select manual. This brings up a list of your partitions. Select the one you want to install ubuntu on, you should be able to tell which one by the size. And from there on you should just have to wait until its done.

I think ive mentioned everything, but if you have any problems just ask :)

I looked up how to do it with a USB - what I found says that you don't "burn" you just copy the files right on to the USB drive.  Also, my computer can boot from USB - so I booted from USB with copied files from ubuntu ISO and it said:

"boot error - replace disk and press any key"

any ideas??

---

### Post by sandyd on 2009-06-07
> **copan said:**
> I looked up how to do it with a USB - what I found says that you don't "burn" you just copy the files right on to the USB drive.  Also, my computer can boot from USB - so I booted from USB with copied files from ubuntu ISO and it said:

"boot error - replace disk and press any key"

any ideas??
WRONG
you mist also copy the boot info that comes on the cd

copying the files doesn't copy the boot sector

why don't you just make life easy and burn a cd?

---

### Post by sailthesea on 2009-06-07
Firstly you will need to set up the installation you want to use If you have dfragged and partitioned your disk with Vista then make sure your USB  or CD has the right image of ubuntu that you want on it and go for a dual boot but be sure to read up on what to do! 
 The forums are of great help but need to be searched carefully 
 Welcome by the way and have a good experience Don't rush!!

---

### Post by copan on 2009-06-07
> **carlee said:**
> WRONG
you mist also copy the boot info that comes on the cd

copying the files doesn't copy the boot sector

why don't you just make life easy and burn a cd?

unfortunately life isn't easy for copan, carlee... my dvd-r and cd-r do not write cd's.  how do i copy the boot sector?

---

### Post by Toshubu on 2009-06-08
Hi Copan,
I suggest you follow Therion's advice in post #2:  study up on (google) **Unetbootin  ** (to review how to prepare the flash drive and **go to the link given** to find out how to prepare the existing windows drive. Then you'll have to get into the computer's bios and make sure you have it set up to boot from a usb port (if it will).

---

### Post by copan on 2009-06-08
> **Toshubu said:**
> Hi Copan,
I suggest you follow Therion's advice in post #2:  study up on (google) **Unetbootin  ** (to review how to prepare the flash drive and **go to the link given** to find out how to prepare the existing windows drive. Then you'll have to get into the computer's bios and make sure you have it set up to boot from a usb port (if it will).


Thank you, for now I have used Wubi and it seems to have worked.. When or if I do a reinstall I will use this advice, and more importantly, I'll try not to rush.  I bet there's a lot I've missed out on growing up - I've been spoiled with the abundance of GUI's.  I want to learn how to use the Linux terminal.

---

