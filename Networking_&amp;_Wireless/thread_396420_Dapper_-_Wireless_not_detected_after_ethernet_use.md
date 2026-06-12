---
title: "Dapper - Wireless not detected after ethernet use"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Tom1942 on 2007-03-29
I am new to Linux but have 25 years experience with windows and some unix work on sparc w/s.  I have installed Ubuntu 6.06 LTS Dapper Drake as the only o/s on an Acer Aspire 5570-2792, dual-core, 1.60 ghz, 533 mhz fsb, 1mb L2 cache, 512 mb memory laptop.  The wireless card is an Atheros (I don't have the model as I am on the road.  I tried SysInfo but could only get this -"ler: Atheros Communications, Inc.: Unknown device 001a (rev 01))".

I have installed ubuntu dapper twice.  The first time I had everything working well using the wireless card on my home lan.  I then decided to make sure the ethernet connection worked (new laptop just received by mail) and when I went back to wireless the card could not be detected.  I searched these forums and tried several solutions but finally the only thing to do was reinstall ubuntu dapper.  I then used only wireless for two weeks on my home lan and even connected it to an access point on the road.

Today I arrived in a motel, connected via ethernet as it was all there was, and worked fine.  I then decided to check to see if there were any access points and the card was not detected.

I wouldn't mind knowing what is causing this, but better would be a solution that does not require another install - I thought I left that all behind with windows.

---

### Post by Tom1942 on 2007-03-29
I forgot to include in the above post the results of lspci:

000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03 )
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Grap hics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Co ntroller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co ntroller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg e (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev  02)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4352 (rev 14)
0000:0a:03.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0 01a (rev 01)
0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b

---

### Post by stchman on 2007-03-30
> **Tom1942 said:**
> I forgot to include in the above post the results of lspci:

000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03 )
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Grap hics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Co ntroller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port  3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Co ntroller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridg e (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev  02)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4352 (rev 14)
0000:0a:03.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0 01a (rev 01)
0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b

Ok, I am going to assume a few things here.  First off is the wireless card built in?  If yes then you need to do a couple of things.

1.  Intall the restricted kernel from the synaptic package manager.  Go to synaptic and type Atheros and there should be a kernel that is ready for madwifi (atheros drivers).

2.  Follow a procedure I laid out on my website [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

This will get your atheros card up and running with encryption capability.  It did on my laptop.

I hope this helps.

---

### Post by spd106 on 2007-03-30
It might be worth checking the compatibility here [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

---

### Post by Tom1942 on 2007-03-30
[COLOR="Red"]spd106 & stchman[/COLOR]:

The wireless card is built-in and is an Atheros AR500G. I checked [COLOR="Red"]spd106's [/COLOR]compatibility list and only found AR500nG models where n is a number like 2, 4 and 5.

The confusing thing about compatibility is that the wireless card worked for as much as 2 weeks at a time before not being recognized.

The next thing I'll do is follow [COLOR="Red"]stchman's[/COLOR] suggestion since the wireless card is internal.

While doing some further troubleshooting I also noted on boot up that Ubuntu showed as 'failed': Starting Basic Networking, Setting Sensor Limits, and Configuring Networking.

As soon as I try [COLOR="Red"]stchman's[/COLOR] suggestion I'll report back.  

Thanks for the help.

---

### Post by Tom1942 on 2007-03-30
[COLOR="Red"]stchman[/COLOR]:

I followed the directions you recommended and made it to the "make" commands but could get no farther.  Here are the results beginning with the last successful command.

root@my-laptop:/usr/src# cd /usr/src/madwifi-0.9.3

root@my-laptop:/usr/src/madwifi-0.9.3# make clean
/bin/sh: line 0: cd: /lib/modules/2.6.15-28-386/build: No such file or directory
Makefile.inc:66: *** /lib/modules/2.6.15-28-386/build is missing, please set KERNELPATH.  Stop.

---

### Post by spd106 on 2007-03-31
Try this command ```
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
```

Then run make again.

---

### Post by Tom1942 on 2007-03-31
Here is the result, it did not seem to work:

my@my-laptop:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
Password:
my@my-laptop:~$ cd /usr/src/madwifi-0.9.3

my@my-laptop:/usr/src/madwifi-0.9.3$ make
/bin/sh: line 0: cd: /lib/modules/2.6.15-28-386/build: No such file or directory
Makefile.inc:66: *** /lib/modules/2.6.15-28-386/build is missing, please set KERNELPATH.  Stop.

---

### Post by spd106 on 2007-04-01
Check that you have the correct version of linux-headers package installed. You will need the one for the 2.6.15-28 kernel, i.e. the one you are using. It should be enough to have the linux-headers-386 package, but that doesn't always work. I suggest you open Synaptic and have a look there.

---

### Post by Tom1942 on 2007-04-03
Thanks.  I'm on the road and have a brief chance to connect using ethernet.  Have only had wireless possibility last few days but as you know that isn't working yet.  Will be home tomorrow and then will try above and post results.  Appreciate the support.

---

### Post by stchman on 2007-05-01
> **Tom1942 said:**
> [COLOR="Red"]stchman[/COLOR]:

I followed the directions you recommended and made it to the "make" commands but could get no farther.  Here are the results beginning with the last successful command.

root@my-laptop:/usr/src# cd /usr/src/madwifi-0.9.3

root@my-laptop:/usr/src/madwifi-0.9.3# make clean
/bin/sh: line 0: cd: /lib/modules/2.6.15-28-386/build: No such file or directory
Makefile.inc:66: *** /lib/modules/2.6.15-28-386/build is missing, please set KERNELPATH.  Stop.

You need to have build-essential installed.  Make will use gcc to compile C programs and the build-essential is needed to compile C programs.  This is an oversight for the Ubuntu makers to not have build-essentials installed by default.  To install that package do the following.

sudo apt-get install build-essential

Also make sure the madwifi files are in the /usr/src folder.

What kernel are you running?  You also need to have a madwifi compatible kernel.  Go to synaptic and type Atheros and this will show you the list of compatible kernels.  I have only tested the procedures on Edgy but they should work for Dapper if you have a madwifi compatible kernel installed.

---

### Post by Mark_in_Hollywood on 2007-07-24
> **stchman said:**
> You need to have build-essential installed.  Make will use gcc to compile C programs and the build-essential is needed to compile C programs.  This is an oversight for the Ubuntu makers to not have build-essentials installed by default.  To install that package do the following.

sudo apt-get install build-essential

Also make sure the madwifi files are in the /usr/src folder.

What kernel are you running?  You also need to have a madwifi compatible kernel.  Go to synaptic and type Atheros and this will show you the list of compatible kernels.  I have only tested the procedures on Edgy but they should work for Dapper if you have a madwifi compatible kernel installed.

I have looked in /usr/src and find no evidence of madwifi files what-so-ever! How do I populate /usr/src with the correct files?

---

