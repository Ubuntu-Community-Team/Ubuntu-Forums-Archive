---
title: "problems with ndiswrapper and install of wg111t usb dongle"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by promethianclay on 2007-08-06
hey, im new here and with ubuntu, so i apologize for both my inability and the fact that this will be the sixth new posting related to this subject, but the others did not solve my problem.

i am attempting to use the Netgear WG111T USB wireless dongle with Ubuntu 7.4 -- a relatively fresh install on an old (sacrificial) Dell laptop. i have followed all the guides i could and installed ndiswrapper using the add/remove function, the synaptic package manager, and even the terminal (although the latter made me nervous, i was using guides mostly from this forum). finally, after many failed attempts and major outburts, i discovered a guide: (( [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) )) and this seemed to be the easiest and most in-depth explanation of the process. following it's directions i started a fresh install of ndiswrapper through the package manager (one at a time, common(already there, as explained) utilities, and then ndisgtk, the graphical front end) i then followed the directions and blacklisted the three processes mentioned in the article by using the terminal. i rebooted. i attempted to install the *.inf files ( athfmwdl.inf and netwg11t.inf, as supplied and verified by the website, the ndiswrapper records, and the members of this forum).  i did this through the graphical front-end, but once installed they did not appear in the list on the left. so, following those directions, i went through the terminal and used the [ ndiswrapper -l ] command to check on the drivers/hardware, only for the terminal to spit back out "invalid driver!" for both *.inf files. now, that can't be...those are the same files that work for everyone.

so, does any one know my problem? did i make a mistake? is that guide only for edgy? do i need to downgrade distros? is there something particularly wierd about Dell laptops ((inspiron 1000 from several years ago))? i am not terribly technical, but if it is all spelled out i can hopefully manage...

please, if anyone can help i would greatly appreciate it, i've been screwing around like this for several days and am leaving on a trip wednesday morning, a trip i would like to take my laptop (with wifi access) along for...

---

### Post by moore.bryan on 2007-08-06
*what is the output of ```
sudo lspci
```?*

---

### Post by kevdog on 2007-08-06
Alright --

There are a lot of things wrong with what you are doing, and I know it will be a struggle to get your USB device to work.  Please hang in.

Facts:
I think I found the link off the ndiswrapper website for your stick:
```
#
Card: NETGEAR WG111T

    *
      Chipset: Atheros USB
    *
      encryption: WPA-PSK (TKIP)
    *
      usbid: 1385:4250
    *
      Driver: Netgear windows driver Version: 21/06/2005, 1.2 from http://www.netgear.de/download/WG111T/WG111T_GRV1.2.zip
    *
      Other: This driver comes with two sets of .inf and .sys files: athfmwdl and wg111t. Both of these must be installed with their *.inf files.

```

Problem
#1. Using ndiswrapper, ndis-gtk from repository is definitely not what you want to do.  The reason is that these are very old versions, and could potentially lead to problems.  So part of the solution is for you to uninstall ndiswrapper (what you have), and reinstall a newer version (from source files).

Here is how to uninstall your current ndiswrapper version:
**[SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE]**
Ok before installing the new ndiswrapper packages we need to uninstall the old version completely. Dont worry if some of these commands dont do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

Here is how to install the newest version of ndiswrapper:
**[SIZE="4"]Download, Compiling, Installing and Configuring Ndiswrapper from Source Files[/SIZE]**

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


OK next we want to download the ndiswrapper source files (Reference URL = _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_)

We are grabbing ndiswrapper-1.48-rc1

```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 
cd ndiswrapper

```

Extract, compile, and install ndiswrapper
```
tar -zxvf ndiswrapper-1.48rc1.tar.gz
cd ndiswrapper-1.48rc1
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Window's wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running

Post back with any questions you have or errors you get.  I would be happy to help you:)

---

### Post by promethianclay on 2007-08-07
thank you, Kev-dog, it worked! awesome, now my laptop is actually functional!
good thing for the forum that you posted, too, your directions are the most clear of those that i've found... nevermind the fact that they are also the only ones that work

---

### Post by kevdog on 2007-08-07
Glad they worked for you.  Congratulations on installing things from source files.  This will be a useful talent that you probably will rely upon in the future (compiling, installing).

---

### Post by jcobbers on 2007-08-18
Prior to installing ndiswrapper, you need to execute: 'sudo make uninstall' repeatedly until nothing is removed. 

Otherwise you may get an error when you run ndiswrapper -v like the following:
```
y@hilbil:~/ndiswrapper-1.47$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename: /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.38
vermagic: 2.6.20-15-generic SMP mod_unload 586
You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
```


So remember: before running make distclean, run make uninstall again and again and again, until it's not doing anything.

```
j@ub1:~/usr/src/ndiswrapper/ndiswrapper-1.48rc1$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper-buginfo
removing /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko

```

```
j@ub1:~/usr/src/ndiswrapper/ndiswrapper-1.48rc1$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
```

---

### Post by Dukey on 2008-02-17
Kevdog, you are a star.  I've been trying for 6 months to get my WG111T to work with Ubuntu, and now thanks to you I'm on line.  Thank you.:)

---

### Post by Guitaraholic on 2008-02-27
Ive followed the guide and had problems with the following command.

when i type in 

sudo modprobe ndiswrapper


my system freezes and i have to reboot!
so i carried on with the installation without it n now im having to reinstall ubuntu bcause im getting a linuz kernal not syncing error on boot!

any advice?

gonna start the whole thing again nows!

---

### Post by Guitaraholic on 2008-02-27
still getting the exact same error on a total clean reboot......

is there any reason for this?


cant understand were im goin wrong at all!

---

### Post by Zzzach on 2008-03-02
Netgear doesn't make 64-bit drivers. Does this mean it's impossible to get it to work on 64-bit ubuntu?? I've tried for like 2 hours and no luck! I need to get this working.

---

### Post by Hightide on 2008-03-02
Hi
I managed to get a netgear WG111 v2 usb to work on my 64 bit machine after I reinstalled Gutsy  It worked right away. . Dont ask me how but its fine.

regards
:)

---

### Post by control_guy on 2008-03-17
Very nice kevdog. Your tutorial solved my problem with WG111T within 15 minutes. Linux spirit is ever stronger with guys like you.

Thanks again.

---

### Post by vx1 on 2008-03-27
Can someone please explain what to do after the restart?

I followed the instructions and everything seemed to go smoothly, but after shutting down and restarting... nothing seems different?  Do I have to do anything else?

Also, what if I am using WEP encryption?  I did turn it off for a while, but I'd really rather not have to do that, since others are connected to the network and I'd rather not mess things up for them.

---

### Post by MadJerry on 2008-03-28
I got to the part where I type:

make distclean

It seems to run ok but then when I type "make" I get the following output, which seems to be an error as when I try and check the version in the next step it tells me ndiswrapper is not installed:

make -C driver
make[1]: Entering directory `/home/madjerry/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C /usr/src/linux-headers-2.6.24-12-generic SUBDIRS=/home/madjerry/ndiswrapper/ndiswrapper-1.48rc1/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/madjerry/ndiswrapper/ndiswrapper-1.48rc1/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/madjerry/ndiswrapper/ndiswrapper-1.48rc1/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/madjerry/ndiswrapper/ndiswrapper-1.48rc1/driver'
make: *** [all] Error 2

I stopped after this as I dont think it will do anything if I go on...

---

