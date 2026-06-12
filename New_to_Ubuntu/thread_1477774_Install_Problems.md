---
title: "Install Problems"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Ericpode on 2010-05-09
Hi
If you can solve this one you may  stop Ubuntu picking up the annual Barge Pole Award?
I have spent >20hrs over the past fortnight trying to install 9.10 and 10.04. I have tried a disc from a magazine, I have downloaded both versions from the website and burnt discs, I have tried two different cd drives. I have tried booting from USB. The best achieved was a partial installation that would boot and then hang after at most 3minutes. I have finally managed to remove it and GRUB but only after updating BIOS downloading several utilities.
System details CPU Intel Quad Core, 4G RAM, 500G and 80G hard drives. The idea was a dual boot system with Ubuntu on the 80G drive and XP on the 500G drive. 
Please remember that advice that requires entering code also require a Linux system capable of running for more than 3minutes.
Regards
Eric

---

### Post by TheHitman2010 on 2010-05-09
If Windows is your primary system, and you want a dual boot system, (like me), try two things:

1) Download Magic ISO, install it, then download the Ubuntu .iso file and mount using Magic Disc.

2) Download the .ISO file, extract it into a folder using the same program above, and run from there. BUT DO THIS IN THE SAME FOLDER YOU HAVE DOWNLOADED YOUR .ISO FILE and do not delete it. Keep it in the same directory. For some reason it likes that.

Give it a try.

---

### Post by TheHitman2010 on 2010-05-09
Then try looking here. It may help you:

[http://ubuntuforums.org/showthread.php?t=1477777](http://ubuntuforums.org/showthread.php?t=1477777)

---

### Post by ranch hand on 2010-05-09
Sounds rough.

We need a wee bit more information though.

What is your video card?  That really does make a big difference.  It would be nice to know if you have a card, and if so what is your integrated video controller.  It is probably intel.

One thing that may let you run the CD, at least is to go back to your bios and disable your card so that the controller takes over.

While you are there I would turn off your MS HDD.  This way you can install without screwing around with worrying about the MBR at all.  When you have an operating system it is easy enough to fix grub to boot both.  Or you could just unplug the MS drive.

I do not know if you have tried any of the boot options that you can get to with the F keys on the 9.10 CD.  This may help.

On 10.04 you need to hit any key when you see the purple screen with the 2 cryptic symbols on the bottom of the screen to get to that type of menu.  I know, we couldn't figure it out in testing either.  Seems a little silly.

As you can see in my sig, our systems are similar.  Mine loves Ubuntu.  I think this is all downto a video problem.   If you use an ATI card I may be able to help.  If nvidia, hopefully some one that knows something about it would be good.

I really would segregate the drives until this is straight.

---

### Post by Ericpode on 2010-05-09
Hi
Thanks for the suggestions. I shall have to give them ago at some point.
Ranch Hand. video card is NVIDIA GeForce 9500 GT and the integrated controller is an Intel one. Yes I tried some of the boot options for 9.10 and yes on 10.04's purple screen I got the hit any key trick eventuually.
Eric

---

### Post by ranch hand on 2010-05-09
I remember folks with that card and I think they were using a different version of the driver.  I would try it with it intel controller and see if that makes a difference.  I keep threatening to do that on here just to see what happens.

You may want to use the search function to search this test forum (archived);

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

I would search for your card and if that doesn't get it just for nvidia.  This should pull up something to help both with booting the CD and making it work and getting your card to work when installed.

---

### Post by Ericpode on 2010-05-09
Hi
Thanks for the ideas, Ranch Hand it looks as if the video card could be the problem and I noticed that NVIDIA offer Linux drivers for their cards on their website. I will give your suggestions a go next time there is a wet weekend round here.
Eric

---

