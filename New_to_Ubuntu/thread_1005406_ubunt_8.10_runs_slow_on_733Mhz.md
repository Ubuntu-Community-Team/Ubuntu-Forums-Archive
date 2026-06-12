---
title: "ubunt 8.10 runs slow on 733Mhz"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by wally123 on 2008-12-08
Hi there,

I Have a problem.
One of my computers is a Dell optiplex GX110, 733Mhz, 256Mb. Windows xp was installed and it was fast enough for me.
I switched to ubuntu 8.10 and it runs as slow as from a livecd.

Does enyone know what could be the problem?

Thanks

---

### Post by lovelyvik293 on 2008-12-08
You have the low configuration and so for optimised performance just remove the software you don't want.

---

### Post by linux6994 on 2008-12-08
Best bet is to put as much RAM as possible in there, the more RAM the better. RAM RAM RAM RAM

---

### Post by stefangr1 on 2008-12-08
> **linux6994 said:**
> Best bet is to put as much RAM as possible in there, the more RAM the better. RAM RAM RAM RAM

Can you post the results you get when you type "top" in a terminal?

And: can you be a bit more specific about what you see as "slow"?
I mean, bootup, specific software etc..

The previous comments are very valid, more RAM is always better, but it does not explain why your system appears to be slower in Ubuntu than it were in Windows-XP, especially since you do have the minimum required RAM. A tip is to get Xubuntu (which is lighter), but Ubuntu should also work in principle.

---

### Post by prshah on 2008-12-08
> **wally123 said:**
> 
One of my computers is a Dell optiplex GX110, 733Mhz, 256Mb. Windows xp was installed and it was fast enough for me.
I switched to ubuntu 8.10 and it runs as slow as from a livecd.


suggestions:[indent]
- Turn off desktop effects (System-Preferences-Appearance-Visual Effects-None)
- Turn off "Tracker" (File Search and Indexing tool) from System-Preferences-Session (Uncheck the entry to prevent it from starting up the next time)
- Use a little lighter version called Xubuntu
- Use a lighter browser such as Galeon
- Consider reducing the DefaultDepth to 16 bit instead of 24 bit (post back for detailed instructions)
- Consider using only one panel instead of two (top and bottom bars)
- Remove the wallpaper and replace with a simple pattern or solid color
- Check your BIOS settings to see how much RAM is taken by the graphics card; reduce to 4Mb or 8Mb if possible (good enough for 1024x768 16 bit).
- Click on System-Administration-System Monitor-Processes-Memory (twice). Now see which processes occupy the maximum memory. Consider getting rid of memory hog programs and replacing with lighter versions. Post back with names if you want suggestions.
- Make sure you have swap enabled (At least 512Mb). Look in System Monitor-Resources-"Memory and swap history".
[/indent]

All said and done, there's just so much you can do with 256 memory. My Fujitsu had 512Mb RAM and run XP Home very well, but Ubuntu was sluggish (comparatively) on it; upgrading to 1Gb has made a HUGE difference in performance.

---

### Post by Tom--d on 2008-12-08
Download and use Xubuntu. Its made for slower computers.

---

### Post by LowSky on 2008-12-08
733Mhz isn't really that fast, I have a laptop running only a 1Ghz and it is slower than my brand new desktop, but it's not like I'm waiting years for it to boot or to run pidgin or Firefox. Windows also runs slow on that machine. But trying to compare a 7 year old Windows OS to a brand new Linux Os is like comparing a 2001 Ford to a 2008 Toyota, there is going to be differences.

Most likely Tracker is bogging the system down, also turn others thing of like bluetooth, and evolution reminder, all this is under system>preferences>session

---

### Post by LowSky on 2008-12-08
> **Tom--d said:**
> Download and use Xubuntu. Its made for slower computers.

I would suggest Debian Linux if you want lighter weight distro.
Ubuntu is nice but its heavy compared to Debian. Debian with Gnome runs much better on lower end equipment than Xubuntu.

---

### Post by =CelticRaven= on 2008-12-08
> **Tom--d said:**
> Download and use Xubuntu. Its made for slower computers.

I dual booted between Win XP and Xubuntu Feisty until a few days ago on an old laptop (1.4GHz, 256Mb Ram) and it was pretty quick. Despite Feisty being a good few years newer than Win XP, the speed between the two was comparable.

Unfortunately the repositories for Feisty have recently become unavailable so I upgraded to Gutsy over the weekend. While it's a little slower it's still very useable and runs at about the same speed as Win XP SP2 with anti-virus and anti-spyware pgms running.

733Mhz might be a bit too slow though. I've experimented recently with Linux on other lower end laptops and found DSL (Damn Small Linux) or Puppy Linux to be good alternatives for old hardware. DSL is Debian based (I think) so is similar to configure to Ubuntu and there's a lot more support available but Puppy Linux is a bit different. I did like Puppy - it was very quick to configure and seemed to be more user friendly initially (especially with wireless network setup) and it was prettier "out of the box" but ultimately I felt it lacked the versatility, software, and online support that you can get with DSL. 

You could also try Fluxbuntu which might look a bit prettier than Puppy or DSL, and may still run at a decent speed on your hardware.

Cheers

---

### Post by halitech on 2008-12-08
> **LowSky said:**
> I would suggest Debian Linux if you want lighter weight distro.
Ubuntu is nice but its heavy compared to Debian. Debian with Gnome runs much better on lower end equipment than Xubuntu.

+1 on going Debian. I have 3 systems here (2 much lower then the OP) runninn Debian with XFCE4 and both are usable. 

nice thread on doing a minimal install of debian with xfce

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by kestrel1 on 2008-12-08
Have a look at the link:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
The recommended Ram isn't being met by your machine & the CPU is a bit near the knuckle. Xubuntu, Puppy Linux etc are better for low spec machines.
I think Debian may struggle:
[http://www.debian.org/releases/stable/i386/ch03s04.html.en](http://www.debian.org/releases/stable/i386/ch03s04.html.en)

---

