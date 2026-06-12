---
title: "Blank screen on install problem"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Sancman on 2010-01-13
I have been trying to install Ubuntu for since about 10am yesterday, done a lot of reading  and searching.....:-k

I have a Dell Inspirion 2650 with 256 mb of ram, HD disk was completly wiped clean, 
the problem I am having is after I boot up the cd I get the first 2 screens 1st being the language selections and then try it or install, I picked install, screen flashes and then I get a flat horzontal line blinking cursor.

nothing happens, freezes up, blank screen.

Any help would be very much appreciated.):P


And the wife thanks whoever can help me, been on this all day and all night.....;)


The amount of knowledge I have about computers is enough to get me into trouble......:P

---

### Post by MyR on 2010-01-13
> **Sancman said:**
> I get a flat horizontal line blinking cursor.

nothing happens, freezes up, blank screen.

Welcome to the forum!

This may sound silly, but how long have you waited while it appeared to be frozen?  With low RAM it may take a long time to boot the live CD.

You may have better luck with the "alternate" installation CD.

peace.

---

### Post by mbzn on 2010-01-13
It could be that the disc is bad, you could try burning at lower speed. Or if that fails you could drop back to the alternate install cd.

---

### Post by Sancman on 2010-01-13
I've waited anywhere between 15 minutes to and hour, have re-booted several times.
Also burned the cd 2 times once in 15 speed and once in the slowest speed which was 7.

What is the "alternate" installation CD that your speaking of?

Thanks for the help.

Also thanks for the welcome.

---

### Post by Sancman on 2010-01-13
Okay,this is getting frustrating to say the least, but am NOT giving up!:)

Have downloaded the "alternate cd" getting the same results....:(  ](*,)

---

### Post by MyR on 2010-01-13
This problem can be difficult to diagnose.  I have seen many people with faulty burner or optical drives.  It is unlikely that the issue is with the software, given that others have experienced no difficulty installing Ubuntu on that laptop.

Here are some things you can try:
1. Install from a USB drive.
2. Use a different CD burner.
3. Use an external CD drive rather than the internal one.
4. Try Ubuntu 8.04 LTS or Xubuntu or Puppy Linux.

Hope this helps.

---

### Post by Sef on 2010-01-13
> I have a Dell Inspirion 2650 with 256 mb of ram, 

I would download Xubuntu.   Ubuntu really needs at least 384 mb ram, so if you want to install Ubuntu, have at least 512 mb ram.  1 gb would make it very fast.

---

### Post by Sancman on 2010-01-13
> **Sef said:**
> I would download Xubuntu.   Ubuntu really needs at least 384 mb ram, so if you want to install Ubuntu, have at least 512 mb ram.  1 gb would make it very fast.


In fact I am planning on getting 1 gig of ram.....just a matter of a small problem called "money" ....:)

---

### Post by MyR on 2010-01-13
Couple years back I installed ubuntu on a 2.6GHz intel pentium 4 system, 256mb ram, and plenty of swap.  Even visual effects worked!  The live CD didn't work so well though.  Xubuntu is undoubtedly faster.

eBay is great for cheap RAM.

@Sef: Fantastic quote in your sig!

---

### Post by Sancman on 2010-01-13
Xubuntu won't work either, also ran memory test and that passed.
8.04.1 will not even load.....get original error message about OS can not load.

Right now I am trying to do a "undelete" on the HDD and will try to load Ubuntu with windows still on HDD, we'll just have to see what happens.....

As far as buying ram on "flea bay" did it before and got scammed bad, never again....
Found this place for the ram;

[http://www.smsassembly.com/](http://www.smsassembly.com/)

seems to be about the cheapest place I have found.....

---

### Post by Sancman on 2010-01-14
Well, tried to "un-delete" the HDD and seems the the program I used did such a great job.......
Now I'll have to get a re-store disk $40. that I really can't afford....

Anyone have any suggestions as to how to get Ubuntu loaded up and running, please send them on.....
Does anyone think a "crossover cable" would work?
Since I don't have a USB drive or external cd-rom drive those options are out, do have a external 3.5 floppy drive....
Thanks again.

---

### Post by hackerlife on 2010-04-09
Hey man. I have the exact same laptop.
Generally, what I had to do was a Ctrl+Alt+Bckspc to restart X, but that was disabled in newer versions of Ubuntu. What version are you running?
The issue was the driver was enabled, and the proprietary driver that Nvidia gives you is extremely buggy and causes frequent freeze-ups as well.

There are multiple ways to uninstall the driver... I'm no expert, but once you get the black screen (You may even here the Ubuntu drums sound, as all is working fine except for your graphical output) you want to press ctrl+alt+f1 to get into TTY1. Log in with your usual name and password (if you have one...) Then type in 
```
sudo apt-get remove nvidia-glx-96
```
You might even try "purge" instead of remove if that doesn't do it.


Best of luck, as far as I can tell this is a wide spread issue with no fix.

PS.... I almost think that while in TTy1 you could do something like "sudo restart gdm" or something... again, I'm no expert.
Also, if you have to make a new xorg.conf (where all your X settings are stored) you can
```
sudo mvdir /etc/X11/xorg.conf /etc/X11/xorg.confback
```
to rename it to a backup, meaning your compy will recreate a new one, hopefully without utilizing the nvidia-glx-96 driver.

---

### Post by Sancman on 2010-04-24
Hackerlife, tried what you suggested and doesn't work.....
I am trying to install 9.10, had the disk sent to me from Ubuntu and it still does not want to install......frustrating to say the least.:confused:

---

### Post by MyR on 2010-04-24
You can try the latest 10.04 release candidate.

[http://www.ubuntu.com/getubuntu/releasenotes/1004overview](http://www.ubuntu.com/getubuntu/releasenotes/1004overview)

---

### Post by Sancman on 2010-05-02
Just tried to install 10.04 version and get same results.......gives me a choice of starting in Windows XP or Ubuntu and will get stuck in a blinking cursor, freezes up:confused::confused::confused:

---

### Post by herbertportillo on 2010-05-02
Same thing happens to me. I tried running the Lucid when it was in beta from a live USB and the screen would go out of whack. I tried to install the final release  two days ago and the screen still goes insane.

[http://ubuntuforums.org/showthread.php?t=1437820](http://ubuntuforums.org/showthread.php?t=1437820)

---

### Post by Boris308 on 2010-05-15
I have had the same problem with my Inspiron 2650...  The issue is caused by ACPI...  Because these laptops are so old they're not 100% compatible with the newest versions of Ubuntu.  I have found through my experiments that if you follow the instructions in this post you'll have success:

The secret is to turn off acpi. You will need to add acpi=off to the grub config as shown in this thread [http://ubuntuforums.org/showthread.php?t=1348427](http://ubuntuforums.org/showthread.php?t=1348427)

However, keep the instructions in this post handy...  you may have to update the grub loader again as you take on new updates...  If the grub loader is updated, you'll need to make the changes again.

Now with that said...  The other option is to use a lower version of Ubuntu.  I've found that Hardy 8.04 works perfectly with my Inspiron 2650, so I've just installed and stayed with that version.  I only use this laptop for simple web browsing and the occational text document.

Good Luck !!  Cheers !

---

### Post by Sancman on 2010-05-16
Thank you Boris, that worked!
Now to figure out why my wireless card doesn't work......:confused:

---

