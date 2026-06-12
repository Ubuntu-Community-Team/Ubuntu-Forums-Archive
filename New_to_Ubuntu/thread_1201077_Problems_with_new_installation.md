---
title: "Problems with new installation"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by rgroene on 2009-06-30
Okay, I posted here a week or so ago about my wireless card driver, which I since got to work.

Anyway, I recently got a new 250gb hard drive and configured it to dual boot with Windows XP Pro and Ubuntu (Jaunty). I configured it with an 80gb partition for Windows (NTFS), an 80gb partition for Ubuntu (EXT3), and a 90gb partition for files that I wanted to open from both (FAT32). I'm having the following problems

IN UBUNTU:

1. My sound is always really quiet even when I turn it up to full volume. I am using a laptop, so I don't expect it to be that loud, but back when I only had Windows installed, it got significantly louder.

2. When I try to access files on my FAT32 partition with Nautilus, it freezes up. I am still able to access these files from the terminal, from programs, and even from Dolphin (a different file manager).

3. My OS is running pretty slowly--I think it's particularly a problem with graphical rendering because when I press ALT+TAB, it takes about a full second to switch between windows. I am currently running Jaunty. Before this, I only had Ubuntu installed (version 8.10--can't remember the nickname, was it Feisty?), and this was not a problem. Earlier, the system crashed and wouldn't boot up again, but I fixed this problem by running recovery.

IN WINDOWS

1. I can't find the proper driver for my sound card. When I run SysInfo, my audio card is Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev02). The subsystem is Gateway 2000 Device 0461.

2. The graphics look all stretched out, which leads to me believe that my graphics card is not rendering things as it should. My graphics card is Intel Corporation Mobile 945GM/GMS, 943/940 GML Express Integrated Graphics Controller (rev03).



If needed, my system and OS specs are as follows:

250gb Hard Drive
1gb RAM
1.6 GHz processor
Jaunty (9.04)
GNOME 2.26.1
GCC Version 4.3.3

---

### Post by Geoff918 on 2009-06-30
Re: 1) You have sound, so that much is good. What I've found is oftentimes in Linux (and this goes for several distros I use including Ubuntu, and openSUSE the mixer is set low or even off.
So here's my best starting advice:
- Open a Terminal Window (I'm assuming you're fairly attuned to working with Ubuntu as per your language in the posts shows a certain awareness).
- Enter 'alsamixer' [enter] (NO NEED TO BE ROOT)
A pretty DOS--ASCII type graphics screen will come up with your mixing levels. Make sure that the applicable parts are turned up including the master, and the "front" settings.
That should do it if your problem is anything like what I've experienced. And, btw--my sound card is louder in my Linux distros than in Windows.

If that advice doesn't work, there's a pretty good guide found here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Re: 2) Don't know. For someone else, you may want to post the results of the following command 'uname -a' (will output information about your kernel, etc.)

Re: 3) What graphics option(s) do you have set? Do you have any customization? Emerald running? CompIz? Desktop effects turned up/on? Are you using a proprietary driver for the graphics card? I have the exact same graphics card and it runs without any glitch or hesitation (I have no proprietary drivers in use since the last version 8.10 Intrepid Ibex it has native support with the current kernel or something--sorry for the lack of clarity, I've only been using Ubuntu more recently, 8.10 made me run screaming for the hills--but I LOVE 9.04).

WINDOWS:

Erm, Vista, XP, 2000, (ME--AKA The Red-headed step-child) :lolflag:
1) I have the same exact sound card as you do on my system. RealTek drivers work for it. You should check your laptop manufacturer's web site (Gateway?). If not, I have an Acer Aspire 5610 with the same hardware, so you could always go to Acer's website and download either the XP or Vista drivers there for this system (it'll work for ya).

2) Not to be condescending, but is your resolution appropriate for your screen dimensions? e.g. not narrow-screen like 1024 x 768 when it would more appropriately be 1024 x 800 or 1280 x 1024? Second, is it just the desktop background? Because that would simply be a setting in the desktop graphics area to stretch, zoom, center, or something of that nature (sorry, not booting into windows here I'm not a fan of windows at all)

I hope something there helps if not all. Happy hunting!

---

### Post by rgroene on 2009-07-01
UBUNTU

1. Thanks for the tip! The sound is working much better right now. I changed "front" from 81 to 100.

2. Linux ubuntu 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux

3. I'm running Compiz with the following options set: gnome compatibility, negative, enhanced desktop zoom, desktop cube, expo, fade to desktop, rotate cube, viewport switcher, animations, cube gears, window decoration, jpeg, png, svg, text, dbus, mouse position polling, regex matching, resize info, scale addons, session management, video playback, workarounds, extra wm actions, move window, place windows, resize window, ring switcher, scale, shift switcher, snapping windows, static application switcher. I haven't played around with the settings that much (a little bit though), and I don't even know what some of the things do. I'm not sure what driver I'm using, but I'm sure I don't have any proprietory drivers running for Ubuntu as I haven't installed any drivers since I installed it.

WINDOWS

I'm running XP Pro. It's what I was raised on, but I learned about Linux when I got to college, and overall I like it better (I'm currently three years through), and I installed it when my Windows system decided to crash. But I still want to have both operating systems so that I can run software that only runs on Windows. Anyway, I guess you didn't need all of that information, I guess I just like to type things. So, back on topic...

1. I'm a little new to installing drivers, so I may be doing something wrong. But I tried the drivers you suggested, and they did not work for me. For every driver I've tried so far, it went through the installation process and told me to reboot. Upon rebooting, either nothing happened or my OS said that if found new hardware, but things still didn't work. And yes, I do (unfortunately) have a Gateway laptop.

2. Maybe my resolution is the problem, but I assumed that it was ultimately a problem with the graphics driver that the only available options were 800 x 600 and 1024 x 768 (which I currently have it set to). In Ubuntu, my resolution's set to 1280 x 800, and it looks great. I know it's not the desktop background because it's not just my desktop that's stretched out--it's everything.

Anyway, thanks for your help!

---

