---
title: "ndiswrapper freezes up my computer"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by vista on 2006-08-20
I recently upgraded to amd k7 kernel. I wanted to try out my 
usb wireless dwl-g132. As soon as I put in the usb-stick
the computer freezes up totaly. This did not happen before
at all when I was using the 386 kernel.

I ran this command uname -a and got this:

> Linux xxx-desktop 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686 GNU/Linux.

Since my comp is an old amd athlon xp 2100+, why do I have smp preempt
installed? I don't remember choosing that option to be installed.
Isn't that for dualcore computers? Im also experiencing high cpu load
even when idle. Is there a way to disable smp preempt?

I also ran this command: modinfo ndiswrapper

> filename:       /lib/modules/2.6.15-26-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.8
license:        GPL
vermagic:       2.6.15-26-k7 SMP preempt K7 gcc-4.0
depends:        usbcore
srcversion:     40DD0BF42F95DD26FA6A8B5
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)



> top - 23:09:45 up  1:51,  2 users,  load average: 0.36, 0.15, 0.13
Tasks:  90 total,   1 running,  88 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.0% us, 11.3% sy,  0.0% ni, 68.3% id,  0.0% wa,  0.3% hi, 15.0% si
Mem:    255576k total,   251120k used,     4456k free,     6708k buffers
Swap:   746980k total,    18444k used,   728536k free,    78144k cached



---

### Post by xlash on 2006-09-21
I'm having the same problems... sometime it takes 5 min to freeze, sometime 30 sec. There are no dmesg either.

 sudo modinfo ndiswrapper
Password:
filename:       /lib/modules/2.6.15-23-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.8
license:        GPL
vermagic:       2.6.15-23-k7 SMP preempt K7 gcc-4.0
depends:        usbcore
srcversion:     40DD0BF42F95DD26FA6A8B5
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)

uname -a
Linux georges 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux




It is not my computer and I'm trying to really get this DWL-G132 A2 wireless dongle working for my girlfriend. Else, Ubuntu  is working perfectly when ndiswrapper is remove from the modprobe





***EDIT***
On [HTML]http://ndiswrapper.sourceforge.net/mediawiki/index.php/Bugs[/HTML]

> # Try to identify what the problem is and give specific information about what causes the problem. For example, if you are using either PREEMPT or SMP, disable them and see if that fixes it if it does, then mention that the problem is with PREEMPT/SMP depending on the case.
# Not all drivers are known to work with PREEMPT and SMP. USB drivers seem to not work with SMP at all - it is not clear if the problems are with Linux USB layer or NDIS driver or ndiswrapper implementation.

Will try to find how to disable PREEMPT and SMP from the kernel tonight. If any of you already search for it, help is welcome.

---

### Post by Jfoard on 2006-09-22
Ndiswrapper gave me lockups when I switched to kernel 2.6.17, apparently there is some sort of incompatibility, I don't know the details.  Compiling the newest version of ndiswrapper (1.21 at the time) from source solved my problem.  I never had problems with the ndiswrapper version in the repos when I was using the default ubuntu kernel, so I doubt we've got the same problem, but I'd suggest trying the newer ndiswrapper anyway, good luck.

[http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

---

### Post by xlash on 2006-09-24
I decided to update my version of ndiswrapper from 1.8 to 1.23.

For now, it's been a few hours, and Ubuntu did not crash.

HEre are the steps I used for reference purposes. I'll say later if it did solve my problems.

Every steps is taken from this french tutorial [http://doc.ubuntu-fr.org/materiel/wifi/ndiswrapper]("http://doc.ubuntu-fr.org/materiel/wifi/ndiswrapper")


First Uninstall previous version.
```
gksudo gedit /etc/modules
```
and remove ndiswrapper line from the modules to load at boot.

```
sudo modprobe -r ndiswrapper
```
to remove the module ndiswrapper from the kernel


```
ndiswrapper -l
ndiswrapper -e <drivername>
```

First do a -l to see all the drivers that were loaded, then, one by one, remove them with -e and there name

```
sudo apt-get --purge remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
```

To remove the package and other left over files

Finally, you need to reinstall the newest version of ndiswrapper like this :

You'll need to recompile ndiswrapper for your kernel with kernel_headers. To do that, 

```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install dh-make fakeroot build-essential
```
At this point, I needed the Ubuntu DVD because my wireless was down and I didn't had any ethernet link.

Download the latest stable version of ndiswrapper from here [http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")

```
sudo cp Desktop/ndiswrapper_*.tar.gz /opt
cd /opt
sudo tar -xvf ndiswrapper_*.tar.gz
```

The * above is for your ndiswrapper version. If you have more than one version on your desktop, use that number instead

```
cd ndiswrapper_*
sudo make install KSRC=/usr/src/linux-headers-*
```

The second * next to linux headers is because when you install that package  2-3 steps bvefore, you are suppose to have that file in /usr/src


After you can reconfigure ndiswrapper like this :

```
sudo ndiswrapper -i PATH_TO_YOUR_DRIVER/neti2220.inf
```

you reinstall your drivers
```

sudo ndiswrapper -m
``` you can now put a line to load at boot

and finally reload it and test it 
```
sudo modprobe ndiswrapper
```

I'll come back later to say if it worked for me longuer than to type this message:-P

---

### Post by az on 2006-09-24
Are you sure you have the most recent version of the .inf file?

Using an older inf file can cause lockups like that.

---

### Post by xlash on 2006-09-25
It was the latest version of the inf files. Actually it already work flawlessly with Fedora Core 4 and the latest ndiswrapper of this time.


Now, it's been more than a day, and I'm proud to say that the problem was with the version of ndiswrapper.


I'm wondering why Dapper was still packaged with that old ndiswrapper version. Personnally, it forced me to reinstall the OS to ensure that the problem was with that .8 version.

Moreover, I tried putting nosmp on the booting line, and it never disabled SMP in my kernel. So, that may have been a workaround, for which I was unsuccesful.

---

### Post by haw730 on 2007-05-25
I have noticed that I too have experienced a problem with ndiswrapper after adding it to the modules. I thought the issue was related to another error. But after reinstalling ubuntu, I had everything running fine, the install went flawlessly on ndiswrapper, I was also able to connect to the router, everything. But once I ran the commands :   sudo ndiswrapper -m and then gksudo gedit /etc/modules and added the module ndiswrapper, the whole lock up happens. Any reason as to this? Or any link to a forum article that has dealt with this? 
Thanks

---

