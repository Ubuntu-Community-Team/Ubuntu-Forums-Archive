---
title: "Broadcom BCM4401, how do I get it working?"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by Apex-jb on 2007-07-27
I need some help getting my wireless card to work in feisty. I have a Broadcom BCM4401. I look at the past threads on this and they were no help.

---

### Post by Apex-jb on 2007-07-27
I do have a BCM43 series in my other laptop, would the drivers I used for it work for this one?

---

### Post by kevdog on 2007-07-27
You are going to have to use different drivers, and at least for the 4401 card I would recommend ndiswrapper (installed and compiled from source - version 1.47 -- and not from repository).  With the 43xx card you could you either ndiswrapper or the bcm43xx drivers.  For ndiswrapper you will need a copy of the windows xp drivers.

---

### Post by Apex-jb on 2007-07-27
How would I install ndiswrapper from source?

---

### Post by kevdog on 2007-07-27
First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```
I cant remember the exact output but make sure you dont get any errors.

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
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

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.

---

### Post by Apex-jb on 2007-07-27
Ok, Il go ahead an try that tomarrow sometime. Ill post back here if I have any problems or dont understand a step. Reading over it I may be able to understand everything but Im not sure. And thank you for your help.

---

### Post by Apex-jb on 2007-07-28
At the verify the installation step of ndiswrapper
```
ndiswrapper -v
``` I get the following
```
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net

``` Do I need to upgrade anything or am I safe to continue?

---

### Post by kevdog on 2007-07-28
I think you are OK -- want to see something strange -- do that command in a couple of days and notice it will say something different.  Anyway great to see that you have compiled and installed from source.  You basically would do the exact same procedure (minus the installation of build-essential/linux headers) for any single source install again (different program of course)!

Just curious -- I thought the tarball was version 1.47, not 1.38.  Ive seen other people with this strange problem too.  Its like the version supplied was wrong, or version is perhaps incorrectly reported -- you sure you downloaded 1.47??

---

### Post by Apex-jb on 2007-07-28
Im pretty sure I installed 1.47, thats what it was labbled as on the site. If I didnt then they labbled it incorrectly.

---

### Post by Apex-jb on 2007-07-28
Do you know where I can find the wireless driver? I have the restore CDs, its a dell E1505, but I cant find the driver on the driver disc. Can I get it online somewhere?

---

### Post by Apex-jb on 2007-07-28
After looking online all I could find were ethernet card drivers not wireless card drivers. When I run the command ```
 lspci | grep Broadcom\ Corporation
``` I get this ```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

```
So what driver do I need to be looking for? The 1390 or BCM4401?

---

### Post by kevdog on 2007-07-29
Alex 

Here is what I found about your card (the bottom line, just go to dell and download their driver version for 32 or 64 bit windows XP (depending on if you are running 32 or 64 bit):

#
Card: Dell Wireless 1390 WLAN MiniCard (Dell Inspiron E1405, Dell Inspiron E1505, Dell Latitude D620, Dell Inspiron 640m, Compaq Presario V3010AU, V3011AU)

    *
      Chipset: Broadcom BCM4311
    *
      pciid: 14e4:4311 (rev 01, subsys 1028:0007)
    *
      Driver: generally called bcmwl5 [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE), though reporting that R115321.EXE driver does not work for Kubuntu 6.06 LTS 64-bit (Kernel 2.6.15-27),[http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE) UPDATE: The above driver has a mayor security bug, the newest driver is R140747.EXE.
    *
      Alternate 64 bit driver: [http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=us&dlc=en&tool=softwareCategory&product=3210693&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=us&dlc=en&tool=softwareCategory&product=3210693&os=228)

---

### Post by ayenack on 2007-07-29
As far as I know the BCM4401 is a wired network card not a wireless card. I have this exact same card in one of my comps and it worked out of the box for me. So I'm guessing that you have mistaken it for your wireless card which is the Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01). You need to get drivers for this if there are any. Google it and see. Or just visit Dells/Broadcoms web site and download and install with ndiswrapper as before.

Ignore this post as kevdog has just pointed that out.

---

