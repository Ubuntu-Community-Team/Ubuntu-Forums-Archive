---
title: "Going back to windows (plz dont hate me and yes i know i'm an idiot)"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Greemhold on 2010-05-02
[SIZE=3]Guys... First of all plz DON'T hate me after that... i tried to return to windows and delete Ubuntu...
Without knowing of what were  to  come i formated the partition with Ubuntu in it and the OS chooser before the boot... i restarted and faced that there was a problem on booting because it couldn't find the OS chooser... then i came up with the idea that i could reinstall windows ,(7 if it helps).. but no, i couldn't because windows could not find a suitable partition (but it could find the disk , thank god).. AND then i reinstalled Ubuntu AND gave them the whole partition... and of course i can not install windows because the hard disk is no longer NTFS.... Can anyone help me? [/SIZE] :(:(:(:(:(:(:(

---

### Post by mistypotato on 2010-05-02
You'll need to boot with the Windows disk, and use the partitioner in WINDOWS to reset your primary partition to NTFS

Going back doesn't make you an idiot lol.

I use Ubuntu for 90% of my work but there are some things that simply cannot be done in native Linux...such as manage my Garmin GPS and Smart phone....so I have several Ubuntu computers and a few Windows machines.

---

### Post by tica vun on 2010-05-02
So the windows installer can't handle etx4 partitions?

Well, since you've apparently already pissed away any data you might have had on your hdd, you could do the following:

THIS WILL IRREVERSIBLY ERASE EVERYTHING ON YOUR HARD DRIVE!

-Boot into ubuntu liveCD
-Use gParted to delete all partitions on your disk
-Reboot with the windows CD
-Install windows

And nobody is going to hate you if you decide not to use ubuntu. Use what works for you.

---

### Post by sadaruwan12 on 2010-05-02
We don't hate you for using windows I use windows there are things where linux can't handle at that point we use a little bit of windows.

On to your problem whip your HDD cleaning using the gParted in the live CD then install your windows first leave an unpartitioned area to install Ubuntu. After finishing the windows installation start your Ubuntu installation when it ask for a place where to install give the unpartitioned area now you're safe.

After that you'll see the GRUB to select your OS.

---

### Post by Seal Daemon on 2010-05-02
You need to boot from your Windows installation CD - it'll allow you to modify / format partitions as you wish.

---

### Post by RTrev on 2010-05-02
The *adults* here would never judge someone for choosing a particular OS.  I consider myself lucky in that everything I need to do I can do under Ubuntu.  But of course some people can't make the switch yet.  That's just life.  I hope you keep trying it periodically, and eventually, like almost all things in computers, it will get better.

I think Bruce Schneier put it well in his blurb here:

[http://www.youtube.com/watch?v=IoXoHlI86rQ](http://www.youtube.com/watch?v=IoXoHlI86rQ)

Things keep getting better, with the one exception of security.

Anyway, sorry it didn't work out for you this time.  Maybe next time.

---

### Post by Greemhold on 2010-05-02
1) Thank you all for the help , realy
2) I think my self an idiot because of what i did not because i'm moving back to windows
3) Like most pc users i 'm a gamer i installed Ubuntu because of their  reliability BUT unfortunately it is not     that good at this part (or i didn't manage to use them)

---

### Post by Greemhold on 2010-05-02
Thank you all i'm in windows now... problem solved!!! :P :P Thank you all again guys!!!

---

### Post by steveneddy on 2010-05-02
I always say that one should use the software that they are more familiar with and that keeps them productive.

Use what works for you.

---

### Post by Rick B. on 2010-05-02
Greemhold,

Don't worry. Just be cool about WIN. I have two machines: an IBM laptop  with Ubuntu 9.10 which I use and a Dell desktop with WIN XP that my wife uses. After 13 years with WIN and two viruses within 15 months that hijacked my laptop, in spite of doing everything right with antivirus, etc., I just had enough with that as well as freezing, reboots, etc, etc.

If the shoe fits, wear it and don't worry about what Ubuntu users may think!

---

### Post by YogiPaolo on 2010-05-07
No, we (meaning mostly "I") won't spew hate at you for your choice of OS. This isn't the Gentoo community. Yes that was a shot across the bow LOL...

I am an IT professional (desktop support aiming towards network admin) and I use a variety of tools. Our rule is "use what works" and this is highly subjective. 

You might want to keep a linux box around to learn and tinker with. I salute you for trying new things.

I too cannot get my Garmin USB gps receiver to work. Sometimes Linux can be very frustrating, but for me this is part of the fun because I am a bit masochistic.

---

### Post by PhysEcon on 2010-05-07
Don't worry about going to Windows.  I'm a big Windows guy myself.  I use Ubuntu in very few circumstances.  I suggest you look into using the Wubi installer to install Ubuntu IN Windows.  It's much safer in the sense that you don't have to formally partition your hard drive.  If you want/need to uninstall Ubuntu it is as simple as uninstalling any regular program.  It's a much more risk-averse method of using Ubuntu.

---

### Post by McRat on 2010-05-07
A little late, but I picked up some $44 HDD's from Fry's to experiment with Ubuntu.  It's far faster and easier to start from scratch, and if you find hardware issues, it takes 5 minutes to go back.

---

### Post by raydeen on 2010-05-07
You might like to give Virtualbox a try for when you want to experiment with other OS's and still keep your Windows setup. I used to have a dual boot system with XP and Ubuntu 8.04 but after upgrading to 7 (which has at least temporarily restored some of my faith in MS), I opted to make a virtual machine with Ubuntu 10.04. So far it's been great. I even get some 3D acceleration with the current version of VBox.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

