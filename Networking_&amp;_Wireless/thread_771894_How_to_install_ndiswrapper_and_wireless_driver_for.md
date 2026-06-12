---
title: "How to install ndiswrapper and wireless driver for newbies"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by puifais on 2008-04-28
D-Link WUA-1340 USB wireless adapter is used here but it'll apply in general

I'm a new Ubuntu 8.04 user and I got my wireless to work after a day of messing around with the help of many people especially kevdog, so here it goes

There are 2 things you need:  the driver files (.inf and .sys) and the application ndiswrapper.  

_Step1:  Getting the Driver_
To get the driver files, you can do this many ways.  A lot of posts will talk about a program called wine and yadayada, but that's too much problems because getting wine to install isn't the easiest thing when you don't have internet and/or an idea of how terminal works.  So I used another computer with internet connection to go download the driver onto a USB stick first.  Go to Applications > Accessories > Terminal and type down

```
lsusb
```

Look for chipset ID.  It'll look something like this 104c:8400.  Then go to [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/) Find your device and download the driver.  If your wireless adapter isn't listed, find a similar driver (the one with the same chipset ID).  Once you get the driver, you can take it to a Ubuntu computer and try to do everything there using ndiswrapper, or you can cheat.  I installed the driver onto a Windows computer first.  Then I go to the driver folder and copy the files I needed.  In Program Files > D Link > drivers folder, there are several files including Dr71WU.sys and Dr71Wu.inf.  If you are not using this wireless adapter, just look for .inf and .sys files with the same name.  Sometimes, the .sys will be in this folder and the .inf will not.  The .inf can be found in Windows > System32 folder.  Run a search here for the .inf file.  Once you have these 2, copy them to a USB.  

_Step2:  Getting ndiswrapper and installing it_
Go to [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482) and download the latest, stable version of ndiswrapper and save it on your usb.  It's 1.52 when I wrote this thread.  The file extension will be .tar.gz

Now turn your Ubuntu computer on.  Copy the .tar.gz file to your home folder.  Pop in the installation CD.  Wait until the computer starts spinning the disk then type this interminal

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential linux-headers-`uname -r`
```

Careful, the last command isn't a single quote (').  It's a backtick (`).  More commands here

```
tar -zxvf ndiswrapper-1.52.tar.gz
cd ndiswrapper-1.52
make distclean
make
sudo make install
```

Verify the installation with

```
ndiswrapper -v
```

The output should be something similar to the following:

```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.52
vermagic:       2.6.20-16-generic SMP mod_unload 586
```

_Step3:  Installing the Driver_
Make a folder in your home folder called "driver."  Copy the .inf and .sys files and put them in this new directory.

```
cd driver
sudo ndiswrapper -i *****.inf
```

Verify this installation with 
```
ndiswrapper -l
```

You'll get something like
```
dr71wu: driver installed
device (14E4:4320) present (**blablabla alternate**)
```

(write down the bold **alternative** thingy)

Now do this and watch for error messages cuz it'll keep running regardless
```
sudo depmod -a
sudo modprobe ndiswrapper
dmesg

```

You should get something like
```
ndiswrapper version *version* loaded 
```

This will make ndiswrapper associate with wlan0
```
sudo ndiswrapper -m
```

This will make the module loaded everytime you reboot
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

Now you need to stop the **alternative** driver and a few other things.  The codes here will stop the computer from using the files we want to black list.

```
sudo modprobe -r **alternative**
```
(For my adapter, they were rt73usb, rt2x00usb, rt2x00lib so I just repeated this line 3 times and substitute these names each time)

Now the actual blacklisting
```
echo "blacklist **alternative**" | sudo tee -a /etc/modprobe.d/blacklist

```
In addition to the ones you previously inactivated, also do this for bcm43xx, b43, and ssb as well.

Now restart
```
sudo shutdown -r now
```

Once it's back on, go to terminal again and verify by

```
lshw -C network
```

You should get something like

```
*-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10 
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11
```

Make sure it says the driver is ndiswrapper.

That's it!

---

### Post by dmizer on 2008-04-28
you should consider using the command:
```
lshw -C network
```
as, lsusb will only list usb network adapters, and lspci will only list internal network adapters (or pcmcia).  however, lshw -C network will show either, as well as give more information.  the chipset id is located after "product"

while i understand that you are using a usb adapter as an example, you suggest (both in your title, and in your directions) that it can be universal.

also ... there is no reason to build from source unless absolutely necessary.  you can grab the ubuntu official ndiswrapper package either from the live cd, or directly from the repos here:
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common)
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9)
(just replace "gutsy" with whatever release you're currently using)

also:
the output of ndiswrapper -l will look like this:
```
$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
```
blacklisting "bcm43xx" alone may not be successful.  for many cards (including broadcomm) there will be multiple modules that need to be blacklisted.  there's no real easy way to figure out what's what without also looking at the output of:
```
lsmod
```

finally:
running the code
```
sudo shutdown -r now
```
has a tendency to break the window manager's panels in xubuntu, and users may return from the reboot without any working panels.  it's probably safer (and easier) just to tell people to reboot.

---

### Post by Fenris_rising on 2008-04-28
i have an unbranded USB adapter it uses the SiS163 chipset. 10 mins with your tut and my laptop is online with kubuntu free from the linux mag. great tut cheers.

regards

fenris

---

### Post by puifais on 2008-04-28
Thank you, dmizer, for adding on to the thread.  I'm actually super uber new so I pretty much just posted whatever I did to get my stuff working and Fenris_rising here is actually making me really proud of myself today :P

---

### Post by Blastomorpha on 2008-04-30
What if a device doesn't use .inf but .sys driver?
After upgrading (actually I fresh installed) from 7.10 to 8.04, my wireless conection is gone, so I edited my /etc/modprobe.d/blacklist this way:
```
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
```
but that's not enought!
Before upgrading I had a modem related restricted driver enabled...

---

### Post by dmizer on 2008-05-07
> **Blastomorpha said:**
> What if a device doesn't use .inf but .sys driver?

windows (and therefore ndiswrapper) makes use of BOTH the .inf and the .sys files to make a driver function.  the .inf file tells the system how and when to use .sys file (like a script).

the ONLY file(s) that ever needs to be loaded into the ndiswrapper wrapper is the .inf file(s), but the .sys file needs to be located on the system in the same directory as the .inf file so that ndiswrapper can call on it as needed.

---

### Post by ktechman on 2008-05-08
I am quite new myself and the instructions were great but after installing the driver I had no connection. The Network Settings Mgr showed  my wireless connection but would not allow to adjust my configuation the card also showed up in my Network Tools. My solution was to enable "All Supported Apps" in "Add and Remove"  and install "WiFi Radar" and then I was able to configure it with the app. My card is a Zonet 1602A It has a 1M extension cord to expand coverage for up to 326' inside a building. Why you ask; I took my rig on a mini vacation and the wireless card couldn't pick up a signal behind the steel door I was behind inside the hotel I ended up using my ancient laptop on the vanity right outside the bathroom. What a PAIN.........

---

### Post by swaybox on 2008-05-08
Hey, I got to the "distsclean" part and it started giving me errors like: 

loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory

There were a lot more that were similar to those.
Then I went to install and it gave me even more errors:

loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)

Again there were alot more but I didn't want to paste the whole thing.
I'm pretty lost here if anyone could help it would prevent hair loss ;]

---

### Post by swaybox on 2008-05-08
Ohh yeah I also downloaded the .exe file for the drivers and I dont know what to do with them. Should I install on a windows computer and copy the .int files and .sys files over?:lolflag:

---

### Post by scholzilla on 2008-05-09
Thanks for this post, but it's still not working for me. I'm running Hardy Heron on a gateway laptop (64bit) that uses the RTL8187B chipset, which is on the list of supported chipsets. I used ndiswrapper to first uninstall the existing drivers and reinstall the recommended win98 driver, rtl8187b. Yes, the .inf and .sys files are in the same folder. <ndiswrapper -l> gives me:

matt@Darwin:~$ ndiswrapper -l
net8187b : driver installed
device (0BDA:8187) present (alternate driver: rtl8187)

I've tried removing the alternate driver both by following your instructions (using modprobe -r, etc.) and by actually editing /etc/modprobe.d/blacklist file, but it still appears even after restart as the alternate driver when I query <ndiswrapper -l>. 

Furthermore when I do:

sudo depmod -a
sudo modprobe ndiswrapper
dmesg | more

the result is a lot of crap, including many lines of output that say "ndiswrapper (import:242): unknown symbol: blablabla" followed by messages that say:
------
ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
ndiswrapper (load_sys_files:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper
lp: driver loaded but no devices found
-------
Any suggestions are warmly welcomed.

---

### Post by Modern Mogul on 2008-05-13
thanks a bunch, but mine is still not working, i have the RealTek 8185... I followed your tut and here is what i get... 

rick@rick-laptop:~$ ndiswrapper -l
net8185 : driver installed
        devidce (10EC:8185) present

so that one has no alteratives

and then the other one does this...

rick@rick-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL -8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:06:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap list
       configuration: latency=0 maxlatency=64 mingnt=32

And its not working, wifi radar program doesn't pick up anything, I can't ping anything, and the network manager doesn't even show a wireless ability yet... Please Help...

---

### Post by Modern Mogul on 2008-05-14
Ok guys I have a serious problem, I was following the tutorial, I did a complete reinstall and this tutorial was the first thing I did, I am running this on a Gateway MX 3417 I have the AMD64 Hardy version for the desktop...

sudo modprobe ndiswrapper doesn't do anything it just goes to the next line and sits, it doesn't even ask me for a command prompt, it just sits there... so I opened up a new terminal, left that one alone, and went on with the tutorial... When it was time to restart I did, and while booting, it gets stuck at *** Loading manual drivers... **and now I do not know what to do, I can't even get into the system, I will have to do another fresh install just to get back in... whats going on?

---

### Post by lswest on 2008-05-14
i'm not sure about why It's getting "stuck"?  Have you let it sit for a while?  and also - sudo modprobe ndiswrapper will not give you an output if successful.  And: did you run sudo ndiswrapper -m, and add "ndiswrapper" to /etc/modules?

---

### Post by Modern Mogul on 2008-05-14
No I haven't let it sit... 

sudo modprobe ndiswrapper just goes to the next line, it doesn't even prompt me for a command, its as if I just pushed the return button and it is just sitting there... Is it supposed to take a while, and I supposed to wait on that one, at least until it gives me a command prompt...

I ran sudo ndiswrapper -m and it went fine...

also, when i open up another terminal and do dmesg, it gives me this long drawn out answer, and then at the end it says i shouldn't use it becuase it is deprecated... lol, I'm currently reinstalling ubuntu, and now I am going to try the tutorial all over again... Thanks for the quick reply...

---

### Post by afeasfaerw23231233 on 2009-03-03
hi, I have this problem while running this. 

 > sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

What should I do? Thanks!

---

### Post by dmizer on 2009-03-03
> **afeasfaerw23231233 said:**
> hi, I have this problem while running this. 

 
What should I do? Thanks!

Are you absolutely positive you need to install Ndiswarapper from source? It's much easier (and preferable) to add it via:
system > administration > synaptic

Just search for "ndiswrapper" and add it.

The method outlined in this thread is outdated, you should not use it.

---

### Post by smartfreak17 on 2012-06-21
> **dmizer said:**
> windows (and therefore ndiswrapper) makes use of BOTH the .inf and the .sys files to make a driver function.  the .inf file tells the system how and when to use .sys file (like a script).

the ONLY file(s) that ever needs to be loaded into the ndiswrapper wrapper is the .inf file(s), but the .sys file needs to be located on the system in the same directory as the .inf file so that ndiswrapper can call on it as needed.

Hey Dmizer i followed all the steps but ended up with the following error:

@ubuntu:~/Desktop/Driver$ sudo ndiswrapper -i bcmwlhigh6.inf 
installing bcmwlhigh6 ...
couldn't find models section "Cisco" -
installation may be incomplete

---

### Post by Iowan on 2012-06-21
> **dmizer said:**
> 
The method outlined in this thread is outdated, you should not use it.After three years...

Closed.

---

