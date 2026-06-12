---
title: "SSD on Ubuntu 10.04?"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by benyben123 on 2010-11-14
Hello. New here. Pretty new to Ubuntu. 

I bought an SSD. 
I am running Ubuntu 10.04.1. 
I was wandering if I can install my SSD. 

I am asking because I am not sure that Ubuntu supports SSD. 
I have read something about over zealous writing to the drive in Ubuntu. I am worried ):

Also, I have Wikipedia "TRIM" and  found there, that only Linux kernel 2.6.33 supports TRIM. 
I am running kernel 2.6.32-25 (according to a package called Sysinfo which I have installed on my Ubuntu). 

Does this mean I should NOT run Ubuntu from my SSD?

I will appreciate any help on this. 
THANK YOU!

---

### Post by sandyd on 2010-11-14
> **benyben123 said:**
> Hello. New here. Pretty new to Ubuntu. 

I bought an SSD. 
I am running Ubuntu 10.04.1. 
I was wandering if I can install my SSD. 

I am asking because I am not sure that Ubuntu supports SSD. 
I have read something about over zealous writing to the drive in Ubuntu. I am worried ):

Also, I have Wikipedia "TRIM" and  found there, that only Linux kernel 2.6.33 supports TRIM. 
I am running kernel 2.6.32-25 (according to a package called Sysinfo which I have installed on my Ubuntu). 

Does this mean I should NOT run Ubuntu from my SSD?

I will appreciate any help on this. 
THANK YOU!
use maverick (10.10), it uses the 2.6.35 kernel.
If you don't want to upgrade, install packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/)
Anything after 2.6.33 will work properly, I use
```

Gentoo Linux sandyd-laptop **2.6.36**-sandyd-hardened #1 SMP Tue Nov 9 17:33:07 EST 2010 x86_64 Intel(R) Core(TM)2 Duo CPU T6500 @ 2.10GHz GenuineIntel GNU/Linux

```and SSDs work perfectly

THe only difference between Hard Disks and SSDs is 
a) SSDS dont crash if you shut down your computer improperly (don't do it though...)

b) SSDS will write faster ONLY if it is a good SSD. There are people on this forum who have gone out and gotten a crappy SSD only to find out that it has a higher write/read time than their HDD.

---

### Post by Paqman on 2010-11-14
> **benyben123 said:**
> 
I am asking because I am not sure that Ubuntu supports SSD. 
I have read something about over zealous writing to the drive in Ubuntu. I am worried ):


Ubuntu supports SSDs well, I have three Ubuntu machines with SSDs. Reducing disk writes was an issue on early SSDs that lacked wear levelling, but it's not really an issue these days.

> 
Also, I have Wikipedia "TRIM" and  found there, that only Linux kernel 2.6.33 supports TRIM. 
I am running kernel 2.6.32-25 (according to a package called Sysinfo which I have installed on my Ubuntu). 


To enable Trim you need to be running a kernel version higher than 2.6.33, as you've noted. Ubuntu 10.10 Maverick Meerkat ships with a kernel that has Trim enabled. You'll also need to make a small edit to a file on your machine.

Once you've got a kernel of the right version hit Alt-F2 and type:
```
gksu gedit /etc/fstab
```

and add the option "discard" to the partitions that are on your SSD. Fstab can seem a bit confusing at first, if you want help getting the edit right, post up the contents of the file here and we'll show you exactly what to do. You could also read [this guide]("https://help.ubuntu.com/community/Fstab").

It's actually really simple to do, so don't sweat it.

---

### Post by benyben123 on 2010-11-14
> **sandyd said:**
> use maverick (10.10), it uses the 2.6.35 kernel.
If you don't want to upgrade, install packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/)
Anything after 2.6.33 will work properly, I use
```

Gentoo Linux sandyd-laptop **2.6.36**-sandyd-hardened #1 SMP Tue Nov 9 17:33:07 EST 2010 x86_64 Intel(R) Core(TM)2 Duo CPU T6500 @ 2.10GHz GenuineIntel GNU/Linux

```and SSDs work perfectly

THe only difference between Hard Disks and SSDs is 
a) SSDS dont crash if you shut down your computer improperly (don't do it though...)

b) SSDS will write faster ONLY if it is a good SSD. There are people on this forum who have gone out and gotten a crappy SSD only to find out that it has a higher write/read time than their HDD.


Thank you both for the answers!

1. I cannot upgrade to 10.10. 
So I have checked out the link you gave me. But I don't get it. All I have to do is install those packages (I tried all of them, some of them did install, others did not)? And after I install them (which I did), what does it do? This enables TRIM support?
Sorry, i am just new to this.

---

### Post by lightrush on 2010-11-15
In a bit more elaborate fashion you have to:

[LIST]
[*]Install Linux kernel 2.6.35: [http://lightrush.ndoytchev.com/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway](http://lightrush.ndoytchev.com/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway)
[*]Enable TRIM for your Ext4 partitions: [http://lightrush.ndoytchev.com/random-1/howtoconfigureext4toenabletrimforssdsonubuntu](http://lightrush.ndoytchev.com/random-1/howtoconfigureext4toenabletrimforssdsonubuntu)
[/LIST]

I hope this helps. :)

---

### Post by Celoxocis on 2010-12-20
i upgraded my lucid box to the new kernel as suggested by lightrush but after a verify using this guide [http://forums.gentoo.org/viewtopic-t-812509.html](http://forums.gentoo.org/viewtopic-t-812509.html) it still shows the same data when i read the sectors (even after like half an hour)

my SSD does support trim according to:
```
Commands/features:
Enabled Supported:
* SMART feature set
Security Mode feature set
* Power Management feature set
* Write cache
* Look-ahead
* Host Protected Area feature set
* WRITE_BUFFER command
* READ_BUFFER command
* DOWNLOAD_MICROCODE
SET_MAX security extension
* 48-bit Address feature set
* Device Configuration Overlay feature set
* Mandatory FLUSH_CACHE
* FLUSH_CACHE_EXT
* SMART self-test
* General Purpose Logging feature set
* Gen1 signaling speed (1.5Gb/s)
* Gen2 signaling speed (3.0Gb/s)
* Native Command Queueing (NCQ)
* Phy event counters
DMA Setup Auto-Activate optimization
* Software settings preservation
* Data Set Management indeterminate TRIM supported
* = supported
```

the "discard" in my fstab looks like this!

```
# / was on /dev/sda3 during installation
UUID=018e97df-f7e6-4bb9-af17-a7af4aa7deda /               ext4    discard,noatime,nodiratime,nouser_xattr 0 1
# /boot was on /dev/sda1 during installation
UUID=10212d3a-3ec6-4f38-8a24-41464c576b4c /boot           ext4    discard,noatime,nodiratime,nouser_xattr 0 2
# swap was on /dev/sda2 during installation
```

any idea what is wrong?

---

