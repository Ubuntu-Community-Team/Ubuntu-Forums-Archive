---
title: "Install Freeze (Wubi Ubuntu)"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by padrejeff on 2010-01-02
I completely uninstalled Wubi and wante3d to do a clean reinstall.

All firewalls off.

Downloaded Wubi .exe files and started install.

Seven hours later it is still in the downloading iso torrent mode.

Something is messed up. It took no where this long in the previous install.

Any clues? :confused:

---

### Post by stoogiebuncho on 2010-01-07
Did this ever work out for you?

Speeds on torrent downloads can vary, maybe you happened to be downloading during a slow time.

---

### Post by padrejeff on 2010-01-07
> **stoogiebuncho said:**
> Did this ever work out for you?

Speeds on torrent downloads can vary, maybe you happened to be downloading during a slow time.

Never worked.
Let her run for over 37 hour and it was stuck in the same exact place.
Have pretty well given up on the Wubi option, although it worked well for me when I had it loaded as a dual boot.

Don't know for sure what to do with Linux (Ubuntu) at the moment.

Jeff

---

### Post by stoogiebuncho on 2010-01-07
That's unfortunate that it didn't download.  I'm not sure what would have caused it.

But speaking as someone who has used both Wubi installs and genuine installs for years, I'd reccomend trying an honest-to-goodness dual boot.  It's much easier than it used to be, and I have seen a noticeable speed difference on my machine when I installed Ubuntu on it's own partition.  Not to mention the benefits of having it on an ext4 filesystem instead of a ntfs.

Wubi is an amazing acheivement and great for trying out Ubuntu, but if you're wondering where to go next, I'd encourage you to try a full install.  We can help you out if you're unsure of what you're doing.

---

### Post by kansasnoob on 2010-01-07
I think Wubi has major problems right now with Karmic:

[http://ubuntuforums.org/showthread.php?t=1375035&highlight=wubi+kansasnoob&page=2](http://ubuntuforums.org/showthread.php?t=1375035&highlight=wubi+kansasnoob&page=2)

I don't use Wubi so I can't be of more help.

---

### Post by padrejeff on 2010-01-07
Well, lo and behold, I just tried the Wubi install and she is up and running fine. However, I have no wireless, so will need help there.

I also (a few days ago) created a full Ubuntu 9.10 USB stick so I could do the full dual boot install from the stick. How hard is it to do the partitions, etc. and would the wireless work on the full install as compared to not working on the Wubi install.

Jeff

---

### Post by stoogiebuncho on 2010-01-07
> **padrejeff said:**
> Well, lo and behold, I just tried the Wubi install and she is up and running fine. However, I have no wireless, so will need help there.

Sweet.

Most likely way to fix wireless (in my experience):

1) Connect computer to the internet via a wired connection.
2) Restart the computer.
3) Go to System > Administration > Hardware Drivers
4) Enable the driver for your wireless card.
5?) If there aren't any drivers there, restart again.

I don't know why you have to restart, but it seems to work.

> 
I also (a few days ago) created a full Ubuntu 9.10 USB stick so I could do the full dual boot install from the stick. How hard is it to do the partitions, etc. and would the wireless work on the full install as compared to not working on the Wubi install.

Jeff

Wireless support should be the same between Wubi and a full install, so if you can't get it working in the Wubi install, it won't work in the full install either (but I bet we can get it working).

If you want to do a full install I'd recommend burning a CD and installing it that way.  The installer will guide you through the partitions section.  The main thing you will want to make sure of before starting is where your Windows partition is so you don't write over it.  There's a lot of tutorials out there. If you've ever installed Windows before, you will probably find that this is easier.

What version of Windows are you running?

---

### Post by padrejeff on 2010-01-08
> **stoogiebuncho said:**
> Sweet.

Most likely way to fix wireless (in my experience):

1) Connect computer to the internet via a wired connection.
2) Restart the computer.
3) Go to System > Administration > Hardware Drivers
4) Enable the driver for your wireless card.
5?) If there aren't any drivers there, restart again.

I don't know why you have to restart, but it seems to work.



Wireless support should be the same between Wubi and a full install, so if you can't get it working in the Wubi install, it won't work in the full install either (but I bet we can get it working).

If you want to do a full install I'd recommend burning a CD and installing it that way.  The installer will guide you through the partitions section.  The main thing you will want to make sure of before starting is where your Windows partition is so you don't write over it.  There's a lot of tutorials out there. If you've ever installed Windows before, you will probably find that this is easier.

What version of Windows are you running?

I'm using Windows XT on the laptop.

The laptop in question is a Dell Mini Netbook, so I cannot install from a CD (no player). I think the installer on my USB stick might also allow the dual boot option and assist a bit in the partitioning.

I'll play with the wireless on the Wubi install a bit and keep you posted. If I can get it to work, I'll try the full install from 
the stick.

Thanks much!

Jeff+

---

### Post by padrejeff on 2010-01-08
[QUOTE=stoogiebuncho;8629201]Sweet.

Most likely way to fix wireless (in my experience):

1) Connect computer to the internet via a wired connection.
2) Restart the computer.
3) Go to System > Administration > Hardware Drivers
4) Enable the driver for your wireless card.
5?) If there aren't any drivers there, restart again.

I don't know why you have to restart, but it seems to work.


When I attempt to enable wireless driver, I get a "Hardware Drivers" box which states:
"no proprietary drivers are installed on this system"

I have restarted six times, all with the same result.

Jeff

---

### Post by padrejeff on 2010-01-08
I also should add, I do not believe my Mini is connecting to the internet with the hard wire ethernet.

Jeff

---

### Post by garvinrick4 on 2010-01-08
Take wire going from CPU to router out of CPU and plug into netbook. Will only fit one connecter in netbook. 

Always do a version download from ubuntu .iso to desktop which is regular download and BURN it to 
a CD at slow speed. Will take 12 minutes to install instead of 12 hrs.  
 Just put in CD tray and choose Wubi install. Only boot off of CD when want to use Live CD for
repair work to system. 

When uninstall WUBI do in from inside the WUBI folder in C: Drive never from add and remove programs. Has a tendency to leave itself in Windows boot manager with later remove. Will cause
trouble for next install be it WUBI or Partitioning.

Seems to me I so WUBI in a flash drive Live also. So I imagine you can use something simple
like USB startup disk creator to hold your Ubuntu version also. Only need 2 gig flash or so which
is dead cheap nowadays. Will hold up to 4 gig of persistence (improvements and downloads retained). I have even put a whole system on 16 gig formatted like hard drive ext3 with boot in sba1 and / or root in sba2 and swap in sba3 if needed and have flash with 14 gig of
space. It will put itself in mbr as soon as update-grub where as USB startup disks do not.
If you use on someones CPU that already has Linux no problem when pull out of machine grub will update back to where it was. If just a Windows machine will make a GRUB2 can freak some out, this is for 16 gig Flash not USB startup disk creator.

---

### Post by stoogiebuncho on 2010-01-08
> **padrejeff said:**
> I also should add, I do not believe my Mini is connecting to the internet with the hard wire ethernet.

Jeff

Well then this is the problem that we will have to solve first, as the drivers for your wireless card will need to be downloaded off of the internet.

Can you give us more information about what's going on with your wired connection?  Does the same chord work when plugged in to other computers?  Are you connected to the internet through any kind of proxy?

As said above, the easiest thing is usually just to take the ethernet chord that's plugged into your desktop computer (if you have one) and plug it into your netbook.  If there are no proxy settings it should connect automatically.

---

### Post by padrejeff on 2010-01-09
OK, after a few more tries, I am able to connect to the internet via the hardwire ethernet cable and surf perfectly booting in Ubuntu.

However, looking for drivers as shown above still shows no proprietary drivers installed. So nothing to enable and no wirless obviously.

On the Windows side, the wireless connects fully and automatically when booted in Windows OS (Broadcom Wireless Adapter).

What now?

Jeff

---

### Post by stoogiebuncho on 2010-01-09
Try going to System > Administration > Update Manager and making sure everything is updated.  Then I'd restart one more time while connected to the internet and then check the drivers location again.

If there's still nothing there, we'll need to know more about your wireless card.  Open a terminal (Applications > Accessories > Terminal) and enter
```
lspci
``` and post the output back here.

---

