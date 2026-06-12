---
title: "New PC"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by jnmjr on 2010-05-23
Hey all, I'm seriously considering modernizing my Pc's due to the fact they are a decade old. Though most of the hardware is newer because of failure or upgrade, I'm concerned with the MB's age as well as the CPU, I don't know what the life expectancy of these is supposed to be but 10 years may be a stretch, let me say I'm not a gamer and my Pc's are for daily work and surfing, I would like suggestions on a set of components that have no issues with Linux and are fairly up to date, two things I'm set with are NVidia graphics and Soundblaster Sound, my preferred CPU would be an AMD. I can't think of a better place to ask than this forum. THX.

BTW, suggestions on Loptops in the $400-$500 that are Linux friendly would also be appreciated....THX

---

### Post by Silent Warrior on 2010-05-23
Have you examined the Desktop Hardware Compatibility/Incompatibility threads? ;)

Sound card:
Hm... Depending on the specific card, Creative's recent line (XFi) is anything but Linux-friendly, in my experience - I bought my Extreme Music in maybe 2003, and not until Lucid do I seem to have good drivers for it, with all sorts of output-options, Creative being the chief source of the delay. And the fancy I/O upgrade-module thing I bought later, to connect my PS2 using TOSlink? Dead in the water still, as far as Linux/PulseAudio is concerned. Consider... just about anything else, really. ASUS's Xonars have earned some respect, I understand, and I plan to go with one of those for my next soundcard. For further concerns, look at ALSA's list of supported cards, to see what works and what doesn't.
Paradoxically, I think even built-in sound-chips have the best support in Linux. Usually. (At least you'll get loads higher percentage of their functionality than with a recent X-Fi card, I bet...)

Motherboard:
Let your CPU decide. DDR2 isn't going away this month, so if you don't need cutting-edge stuff, don't be afraid of those. Or if you can still find a CPU for your socket, I won't hold it against you.

CPU:
I have yet to hear of a CPU being incompatible with Linux. Just take your pick.

Graphics:
I'm not familiar with Nvidia's lines (all I know is that my 9600GT does the job admirably in everything up to Dragon Age), but I think you can get away with components as old as the 8x00s. Nvidia seems to have better Linux-support for their newer gear than ATI, but since you're not contemplating GTX4x0s (or ATI 5xxxs), I don't think you'll need to worry much about compatibility-issues or driver-support. Have a look at what's comfortably available to you, then decide.

Laptops:
I'm no expert. I can tell you my Toshiba Satellite Pro L300 works just fine, though, besides the fan-issue, the wireless connection breaking if I install backported modules, Toshiba not providing easily Linux-applicable BIOS-updates...

---

### Post by joshedmonds on 2010-05-23
Side note:

If you are happy with the hardware you have, but want to upgrade only because of concerns about hardware lifecycle, you might consider booting from an external USB.

Since the release of 10.04 I have been running from an external 7K rpm 3.5' hard drive over USB 2.0 with excellent results. The hard drive has legacy grub on the MBR for ease of use, and several partitions for multiple distros.

The main PC I boot from is a dual-core 2.8Ghz with a new low-spec Nvidia graphics card with the new drivers installed, however having these activated causes no problems if I boot from another PC.

This setup is suitable for running games such as Aquaria and Penumbra with no noticeable issues. It boots quickly, applications start quickly, and I have had no other issues related to running from a USB drive. The main consideration is putting the drive out of the way as a disconnect could cause data loss.

If you were to install to a new hard-drive and run from USB, any other hardware failure would only impact to the extent you lost work from that session or didn't have access to any other PC or laptop. You could copy your existing install to an external hard-drive, and then copy back to an internal hard-drive if you do upgrade the whole PC.

---

### Post by 3rdalbum on 2010-05-23
> **jnmjr said:**
> my preferred CPU would be an AMD.

Is this due to something you've heard about AMDs, or because you consider Intel to be "the enemy"?

If you're looking at building a computer on the cheap, you have two choices: AMD's Athlon and lower Phenom CPUs, or Intel's slightly-outdated Core 2.

AMD's platform may be a little cheaper at the cheap end, but probably not by a lot. I believe the Core 2s are still faster than what AMD has at the cheap end.

If you're looking at something with a reasonable level of performance for 2010, then you would be mad not to consider Intel. Their Core i5 range is very good, and is only threatened by AMDs top hexacore (6 core) CPU running at 3 GHz. You're likely to be paying more for the AMD hexacore, too.

Now don't get me wrong; I'm going to buy the AMD hexacore when I have some cash. AMD has forward-compatibility, which means that I could just put in an Octocore when they have one (Intel probably won't keep their current sockets for long). But I certainly considered the Intel very seriously. If you haven't... then do so now, because you WILL get better performance for less money at the moderate end of the market.

---

### Post by jnmjr on 2010-05-23
Thanks for the replies so far, keep them coming, also some of you may want to post your system configurations that work well... hey I don't mind  copying one of your systems :)...

Just for your info... My true objective is for a system that will age with grace as is the case with my present one. I'm not one to upgrade unless absolutely necessary.

---

### Post by quadproc on 2010-05-23
> **jnmjr said:**
> Hey all, I'm seriously considering modernizing my Pc's due to the fact they are a decade old. Though most of the hardware is newer because of failure or upgrade, I'm concerned with the MB's age as well as the CPU, I don't know what the life expectancy of these is supposed to be but 10 years may be a stretch,
These days, the shortest lived part of system is usually the disk drives.  They are now considered to be a throw-away commodity.  If you get more than two years from a carefully handled drive then you are doing well.  It would be good to have a robust recovery system available: RAID1, external backup media, etc.
>  let me say I'm not a gamer and my Pc's are for daily work and surfing, I would like suggestions on a set of components that have no issues with Linux and are fairly up to date, two things I'm set with are NVidia graphics and Soundblaster Sound, my preferred CPU would be an AMD. 

One thing that I can tell anyone is that Buffalo offers an external disk which does **not** work with eSATA Linux systems.  Its USB connection works but that is 8 times slower.

The entire graphics arena has become rather complicated in recent times.  Ubuntu is now using an X windows server which is incompatible with older graphics hardware.  The graphics driver area is full of incompatibilities.  You need to make sure that your OS, your X windows, your graphics hardware, and your graphics card are all (will be) compatible with each other.

ATI is bending over backwards to work with the Linux community in graphics cards and drivers, however ATI's legacy stuff is just that, legacy.  It is no longer supported.  But ATI is putting a lot of effort into their new stuff and is working hand-in-hand with the open source community as well as continuing to provide their proprietary driver and support.

Some time ago I evaluated the lifetime of computer systems in terms of support, performance, and available products.  I cocnluded that a system for business use had about a 2 year lifetime while a home system could be lived with for about 4.3 years.  Of course, my criteria may be different than yours so please take this with a grain of salt.

quadproc

---

### Post by Kafubie on 2010-05-23
I am no Computer-building expert, but Intel and Nvidia work well in Linux.

---

