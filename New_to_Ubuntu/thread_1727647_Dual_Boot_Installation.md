---
title: "Dual Boot Installation"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by Hans Upp on 2011-04-12
I want to dual boot Ubuntu + WinXP but I've read a lot in here where most people seem to install windoze **first **then use Wubi , whatever that might be, to install Ubuntu.

I have an existing Ubuntu Maverick installation only ( a learning process) and now I want to add WinXP and ultimately get both to access some common data. 

Please advise what suggestions can you make for doing it that way round.

---

### Post by Rex Bouwense on 2011-04-12
I got a couple of sites for you to check out. 
[https://help.ubuntu.com/10.04/switching/C/dualboot.html](https://help.ubuntu.com/10.04/switching/C/dualboot.html)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Enjoy.
Rex

---

### Post by mikewhatever on 2011-04-12
It doesn't matter really what's installed first.
First, you'll need some unallocated space to create a partition for Windows. Use an Ubuntu live cd to resize one of the existing partitions, or, if you have a free NTFS partition, use that.
You probably know better how to install Windows, so I won't go into that. After Windows is installed, Ubuntu won't be bootable, which is easily solved by reinstalling Grub from the live cd. 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by seawolf167 on 2011-04-14
As previously said, you can install either first. I recommend not using WUBI if you are planning on using Ubuntu for anything but a "test to see if I like it" run. See the 2nd link in post #2 for a how-to on installing Ubuntu after Windows or vice-versa.

---

### Post by Hans Upp on 2011-04-14
Trying to follow the guide . . . fell at first hurdle :sad:

'Resizing a partition' gives me options which I do not understand.

Free space preceeding MiB - ???
Free space following MiB - ???

Align to:  - cylinder? - MiB?  - None?

If I knew what an MiB was it might help.  Then I might know if I want the free space before it, after it, under it, over it, outside it or whatever else it might throw out to confuse the issue.  

and how am I to know if I want it aligned to Cylinder? what cylinder? where is the cylinder?
I know I have cylinders in my car engine, maybe its one of those.

or maybe I have to align it to the MiB,  
ah yes, I remember now, that's Men in Black, isn't it?

I used to find resizing a partition was just, well, resizing   :confused:

---

### Post by seawolf167 on 2011-04-14
Free space <blah> MiB is how much free space precedes or follows a partition

Align to cylinder aligns to a cylinder boundary, this isn't sooo critical as if you don't likely the only issue you'll notice is a tiny bit smaller partition size. Use this if you don't set any MiB space

Align to MiB aligns to the free space preceding/following ending, again, not so critical. Use this if you set MiB space

---

### Post by Hans Upp on 2011-04-14
> Free space <blah> MiB is how much free space precedes or follows a partition[COLOR=Red]but that doesn't help me know whether I ought to make it precede or follow[/COLOR]

> Align to cylinder aligns to a cylinder boundary, this isn't sooo critical as if you don't likely the only issue you'll notice is a tiny bit smaller partition size. Use this if you don't set any MiB space[COLOR=Red]but do I, or do I not set any MiB space?  . . . what IS MiB space? what IS MiB? what cylinder boundary? I am more confused than before.[/COLOR]

> Align to MiB aligns to the free space preceding/following ending, again, not so critical. Use this if you set MiB space[COLOR=Red]Doh![/COLOR]

---

### Post by seawolf167 on 2011-04-14
Essentially, don't worry about them. Leave the default MiB as 0, check to round to cylinder boundaries, set your sizes as needed.

---

### Post by Hans Upp on 2011-04-14
So why does it say (and force) a minimum size of MiB 8116 if you say the default is 0?

---

### Post by seawolf167 on 2011-04-14
Ok I thought we were talking about partition 0. The MiB after the partition will change as you change the partition size (i.e. the greater the partition size, the smaller the MiB free space after and vice versa). All you really have to set on this screen is your partition size information.

---

### Post by oldfred on 2011-04-14
It might be worthwhile to see some examples:

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

There are bytes, kilobytes, megabytes, gigabytes etc. And to add to the confusion some count in 1000 and others in 1024s.

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)
It's the difference between gigabytes (GB) and gibibytes (GiB). One gigabyte = 1000 x 1000 x 1000 bytes (base 10). One gibibyte = 1024 x 1024 x 1024 bytes

---

### Post by Hans Upp on 2011-05-16
That's torn it.

After many (aborted) attempts using gparted I partitioned it to give me a large NTFS partition.

Proceeded to install WinXP to it today. It reached the 'reboot' stage of installation and now I can't get it to boot.

says: file missing or corrupt
<windows root>\system32\hal.dll

but that's where it stops, can't get past it. I've set boot device to CD and it still comes up the same. So it's:  no windows, no ubuntu, no good.

---

### Post by seawolf167 on 2011-05-16
In the future, I highly suggest using the Windows partition editor to partition NTFS, GParted works, but not always perfectly.

As for your boot issue, try putting in the XP install cd, then booting into the recovery console. Once there, type

```
bootcfg /rebuild
```

and restart. This should fix your Windows booting troubles and allow you to boot Windows.

This will also wipe out your GRUB installation, so after Windows is booting fine, you'll have to boot off a Ubuntu LiveCD and follow the instructions here to reinstall GRUB2 which will then point to the Windows loader and Ubuntu partiton.

---

### Post by Hans Upp on 2011-05-16
thanks, but I think you have missed my point.

That IS what I get, whether trying to boot from HDD or XP install CD.

I can't even get to the repair console.

---

### Post by oldfred on 2011-05-16
With XP there are no partitioning tools and the repair tools are somewhat different than those with Vista/7.

But missing hal is almost always not missing hal.dll but something else.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by seawolf167 on 2011-05-16
When you start your computer, look for a message during POST that says something like "Press F12 to Display Boot Menu". This message display may be turned off in BIOS, so just try hitting [F12] or [F10] to enter the boot menu. Then select your boot medium (Windows cd) to boot off of.

If that doesn't work, double check your BIOS settings to ensure that you have the cd drive listed as bootable.

---

### Post by Hans Upp on 2011-05-16
I thought I had explained all that in my first post today.


It is set to boot off CD. The CD drive is bootable (how else did I install WinXP, as far as it went)

But now, whether booting off CD or HDD, it halts at this point:
file missing or corrupt
<windows root>\system32\hal.dll

---

### Post by seawolf167 on 2011-05-16
I understand that you have it set to boot off the cd, but the hal.dll error means that there is a problem with Window's boot.ini file which resides on your Windows XP partition, separate from your Windows cd. This means that your computer is completing POST and attempting to boot to your Windows install. Your Windows cd should boot regardless of the state of the Windows installation (which is why I was seeing if you can get into the boot menu, and select the cd to boot off of, to ensure that it doesn't attempt to boot the installed OS).

---

### Post by Hans Upp on 2011-05-16
deleted

---

