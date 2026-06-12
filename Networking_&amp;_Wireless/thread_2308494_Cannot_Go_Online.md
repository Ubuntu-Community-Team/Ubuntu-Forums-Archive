---
title: "Cannot Go Online"
date: 2016-01-03
forum: Networking &amp; Wireless
---

### Post by fjl001 on 2016-01-03
Hi,

I have downloaded and installed Linux Ubuntu on a desktop that I built years ago, but now cannot go online. I have tried just about everything over the past couple of days and now I badly need help with this problem, before I either go insane or give up on this installation.

The system was quite the thing when I built it but it has fallen behind specifications wise (as all computers do). I had Windows XP on it and it was getting really hard to keep clean of all sorts of malware especially after MS stopped supporting that OS. I built it with quality components and it's still going fine but does not have the horsepower to run newer Windows versions - it has an Intel dual core processor and only 2 Gb of memory - and all components work well within their current limitations. So I loaded Ubuntu 14, 32 bit, on it and the installation went smoothly. It's working well locally, albeit a bit slowly because of the processor speed, but still faster than Win XP used to.

However, here is my problem.  I am using a US Robotics Wireless Turbo PCI Adapter model USR805416 (sometimes referred to as USR5416) in the computer to access my router located on a different floor. I have the latest Windows driver for the Adapter.

I have tried both ndiswrapper and driverloader and can't seem to get anywhere with either proggie! USR5416 is supposed to be compatible with Ubuntu!

Here is a log of the output when I tried using ndiswrapper from the command line:

fjl001@King:~/Downloads/ndiswrapper-1.59$ sudo make install
make -C driver install
make[1]: Entering directory '/home/fjl001/Downloads/ndiswrapper-1.59/driver'
make modules
make[2]: Entering directory '/home/fjl001/Downloads/ndiswrapper-1.59/driver'
make -C /usr/src/linux-headers-4.2.0-16-generic M=/home/fjl001/Downloads/ndiswrapper-1.59/driver
make[3]: Entering directory '/usr/src/linux-headers-4.2.0-16-generic'
  CC [M]  /home/fjl001/Downloads/ndiswrapper-1.59/driver/crt.o
/home/fjl001/Downloads/ndiswrapper-1.59/driver/crt.c: In function â€˜_win_srandâ€™:
/home/fjl001/Downloads/ndiswrapper-1.59/driver/crt.c:470:2: error: implicit declaration of function â€˜net_srandomâ€™ [-Werror=implicit-function-declaration]
  net_srandom(seed);
  ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/fjl001/Downloads/ndiswrapper-1.59/driver/crt.o' failed
make[4]: *** [/home/fjl001/Downloads/ndiswrapper-1.59/driver/crt.o] Error 1
Makefile:1398: recipe for target '_module_/home/fjl001/Downloads/ndiswrapper-1.59/driver' failed
make[3]: *** [_module_/home/fjl001/Downloads/ndiswrapper-1.59/driver] Error 2
make[3]: Leaving directory '/usr/src/linux-headers-4.2.0-16-generic'
Makefile:183: recipe for target 'modules' failed
make[2]: *** [modules] Error 2
make[2]: Leaving directory '/home/fjl001/Downloads/ndiswrapper-1.59/driver'
Makefile:186: recipe for target 'ndiswrapper.ko' failed
make[1]: *** [ndiswrapper.ko] Error 2
make[1]: Leaving directory '/home/fjl001/Downloads/ndiswrapper-1.59/driver'
Makefile:27: recipe for target 'install' failed
make: *** [install] Error 2

With Windows, the PCI card must be installed after the driver is loaded. I don't know how that works with Ubuntu. At present the card is in the PC. I have not pulled it out to install the Ubuntu software. Could that be the problem? Or is there something else that is not working right here?

Thank you for all suggestions.

fjl001

---

### Post by grahammechanical on 2016-01-03
With Linux the hardware device must be in the PC before we install a Linux distribution. That will give a good chance that the hardware device will be detected and a driver module installed. It also helps if the machine is connected to the internet by a wired connection. Then any available drivers can be downloaded during installation.

There should be a Network Manager icon in the top panel (2 arrows going in opposite directions). It has a drop-down menu. Is WiFi enabled? Is there a list of wireless access points? That information will give clues as to whether the WiFI adapter is switched on and has a driver activated.

We can also go to System Settings>Software & Updates>Additional drivers tab and we may find an offer to activate a WiFi driver. We need to be connected to the internet at the time and also allow time for the utility to do it work.

Please run this command & tell us what the printout is

```
rfkill list
```

This is the result that I get

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


It identifies that there is a WiFi adapter present and that it is not switched off by software (WiFi is enabled) and it is not switched off in hardware. There is power going to the adapter and we do not need to use some keyboard combination to switch on the adapter or to enable it in the motherboard BIOS.

Regards

---

### Post by fjl001 on 2016-01-03
Thank you grahammechanical for the prompt reply.

When I installed Ubuntu everything was overwritten, so the Windows driver was gone, also it appears there is no native driver in Ubuntu for this adapter.

When I issued the command rfkill list, a blank line was returned.

I do not have access to the router or the modem to do a wired connection.

I went into the network manager before and entered some information such as access point name and WEP key, but only got an error message that the network was inaccessible on the browser. No access points show up at all in spite of there being numerous in my area.

I do not believe there is any driver installed at all.

---

### Post by fjl001 on 2016-01-03
I should point out that it is actually Ubuntu 15.1 (not Ubuntu 14 as I posted above), 32 bit, that I installed.

---

### Post by Bucky Ball on 2016-01-03
*Thread moved to **Networking & Wireless**.*

Avoid ndiswrapper. What gives you the impression you need it (and if you read it on a website, how old was it)?

Open a terminal and post the output of this here, between code tags, please (see last link in my signature):

```
sudo lshw -C network
```

---

### Post by fjl001 on 2016-01-04
Thanks, Bucky Ball.

I thought I needed something beyond the Ubuntu OS because the network card was not detected and the driver was not installed when I installed the OS. I did some reading online and found that in some situations an additional program is required to make some adapters work - that's when I started experimenting with the proggies I mentioned, but they don't seem to work either! I don't remember what the dates were.

Anyways I've done the command you asked in the Ubuntu terminal. here is the result:

```
fjl001@King:~$ sudo lshw -C network
[sudo] password for fjl001: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: b
       bus info: pci@0000:01:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:fbffc000-fbffdfff memory:fbfc0000-fbfdffff
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: enp1s13
       version: 13
       serial: 00:1a:92:04:8e:69
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:23 memory:fbff8000-fbffbfff ioport:e800(size=256) memory:fbfa0000-fbfbffff

```


OK, if I can get some help with the meaning of network 0 UNCLAIMED ...

---

### Post by Bucky Ball on 2016-01-04
Code tags, please, as requested. ;)

Have you plugged in an ethernet cable and done an update then checked 'Additional Drivers'? You have this:

Texas Instruments ACX 111 54Mbps Wireless Interface

... but there seems to be no driver installed for it. :-k

It appears that card is old? And can be tricky. Have a [look here]("http://askubuntu.com/questions/225858/how-do-i-get-a-texas-instruments-acx-111-wireless-card-working") under the answer heading down the page '4 Answers'.

If you have no luck it may turn out easier to buy a cheap usb wireless dongle and be done with it ... or a readily supported card.

---

### Post by fjl001 on 2016-01-04
Thanks, that's what I thought.

Yes the adapter is several years old, maybe 8 or so but it will work great if there is a driver for Ubuntu to work with it. I read that US Robotics supplied one to have the driver written by the Ubuntu team and that it was supported!

I don't have access to the modem and/or router near this PC. I'd have to drag it lock stock and barrel all to the router which is sitting by the TV on a wall unit a level below, or buy a 50+ foot network cable !!!

I'll follow your link and see where that takes me, but I believe I've been down that road before with no success !!!

Thanks for trying, bud.

---

