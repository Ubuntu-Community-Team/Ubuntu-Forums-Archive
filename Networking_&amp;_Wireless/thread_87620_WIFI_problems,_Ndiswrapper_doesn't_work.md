---
title: "WIFI problems, Ndiswrapper doesn't work"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by lonedar on 2005-11-08
Hello,
I downloaded Ubuntu 5.10, and I've liked it so far.

But I've got a small problem - I can't connect to the internet. 

I dont have access to wired internet, only wireless and dialup, and I cant configure them.

I've got a Fujitsu-Siemens Amilo D 1845 laptop.

Dialup could be a problem, as I've got a winmodem. So I've decided to try to set up the Wifi.

The wireless card is "Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow]"

I've tried using ndiswrapper with the official Windows drivers, as reccomended in [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") (first card under letter G), but it doesn't work - it installs the drivers just fine, the ndiswrapper module also loads, but the graphical net conf tool in GNOME still won't connect.

dmesg output: 

after loading ndiswrapper:
```
[4297520.780000] ndiswrapper version 1.1 loaded (preempt=no,smp=no) 
```

After trying to activate the wireless network interface:

```

[4297544.107000] eth1: resetting device...
[4297544.107000] eth1: uploading firmware...
[4297544.222000] prism54: request_firmware() failed for 'isl3886'
[4297544.222000] eth1: could not upload firmware ('isl3886')
[4297544.222000] eth1: islpci_reset: failure
[4297547.767000] eth1: resetting device...
[4297547.767000] eth1: uploading firmware...
[4297547.859000] prism54: request_firmware() failed for 'isl3886'
[4297547.859000] eth1: could not upload firmware ('isl3886')
[4297547.859000] eth1: islpci_reset: failure
[4297547.909000] eth1: resetting device...
[4297547.909000] eth1: uploading firmware...
[4297548.001000] prism54: request_firmware() failed for 'isl3886'
[4297548.001000] eth1: could not upload firmware ('isl3886')
[4297548.001000] eth1: islpci_reset: failure
```

I'm not sure, but I think that there should be more messages after loading ndiswrapper (about the separate drivers). Is this so?

It's difficult to do anything, because without net access I can't even download additional packages to fix the problem.

Seems strange, as the ndiswrapper wiki list had information about the same card.

Please help.

Edit- "iwlist eth1 scan" doesn't find the access point (which is within range)

---

### Post by xsmind on 2005-11-08
I have the same wireless card on my FS Amilo L1300. And after I've tried to make it work, the results were exactly as yours.
But when I try to enable the card I get this:

```
$ sudo ifup eth0
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Failed to bring up eth0.
```

---

### Post by lupine_nickt on 2005-11-08
By the sounds of it, you need to find a firmware for ndiswrapper to use. That is, the isl3886 module is trying to load a firmware file (due to the firtmware not being on the wlan card), and failing to find it.

Try [http://lekernel.lya-fr.com/prism54_firmware.html](http://lekernel.lya-fr.com/prism54_firmware.html) as a starting point... I've never had the problem, so I wouldn't know exactly what to do, I'm afraid.

xF,

...Nick

---

### Post by mips on 2005-11-08
From [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsFujitsu](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsFujitsu)  try add 'ndiswrapper' to /etc/modules, and 'ndiswrapper -i prisma00.inf'

---

### Post by essexman on 2005-11-08
[quote=lupine_nickt]By the sounds of it, you need to find a firmware for ndiswrapper to use. That is, the isl3886 module is trying to load a firmware file (due to the firtmware not being on the wlan card), and failing to find it.

Try [http://lekernel.lya-fr.com/prism54_firmware.html]("http://lekernel.lya-fr.com/prism54_firmware.html") as a starting point... I've never had the problem, so I wouldn't know exactly what to do, I'm afraid.

xF,

...Nick[/quote]

Nick

It looks odd to me that they are looking at eth0 and eth1.  The ndiswrapper card I loaded went into wla0 automatically, and my rt2500 card is on ra0.  Isn't ethx normally for cabel lan?

Have you seen this before on Ubuntu?

nidswrapper site logs their card as working with 2.6.10 so breezy should be no problem.

---

### Post by lupine_nickt on 2005-11-09
What's in a name? :)  The output given definitely shows it's having trouble with the firmware, though. Maybe try [http://prism54.org/](http://prism54.org/) to bypass ndiswrapper?


xF,

...Nick

---

### Post by lonedar on 2005-11-09
Thanks for the replies, I haven't tried to get the firmware, as I don't have my laptop with me. But I will try that once I get it.

[QUOTE=xsmind]I have the same wireless card on my FS Amilo L1300. And after I've tried to make it work, the results were exactly as yours.
But when I try to enable the card I get this:

```
$ sudo ifup eth0
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Failed to bring up eth0.
```[/QUOTE]

Yes, I got the same thing when i tried 
```
$ sudo ifconfig eth1 up
```


[QUOTE=mips]From [https://wiki.ubuntu.com/HardwareSupp...LaptopsFujitsu](https://wiki.ubuntu.com/HardwareSupp...LaptopsFujitsu) try add 'ndiswrapper' to /etc/modules, and 'ndiswrapper -i prisma00.inf'[/QUOTE]

I did this, only I loaded the ndiswrapper module manually. The driver installs ok.

[QUOTE=essexman]Nick

It looks odd to me that they are looking at eth0 and eth1. The ndiswrapper card I loaded went into wla0 automatically, and my rt2500 card is on ra0. Isn't ethx normally for cabel lan?

Have you seen this before on Ubuntu?

nidswrapper site logs their card as working with 2.6.10 so breezy should be no problem.[/QUOTE] 

Yes, this seemed strange to me as well. But it's only a name - iwconfig recognizes it as a wireless card.

Anyway, I will get my laptop and try to upload the firmware.

---

### Post by lonedar on 2005-11-09
Ok, another problem. 

The programs that should fix the problem need to be compiled first - and it seems that Ubuntu doesnt include make in the default configurations. Is there any way around this?

---

### Post by lupine_nickt on 2005-11-10
'sudo apt-get install make' ?

Make is (I think) on the Ubuntu CD, so you won't need internet access for it.

You'll need to install gcc & all the rest as well, obviously...

xF,

...Nick

---

### Post by cyrano1917 on 2005-11-13
Hello, just a few remarks, for I had a similar problem.

I tried to install the driver for my wireless pcmcia card with the ndiswrapper version included in the ubuntu CD (my card is a WPC11 linksys), and I used the correct winxp driver. When I did "modprobe ndiswrapper" and looked at the system messages with "dmesg" I had only a line saying that ndiswrapper v1.1 was loaded but nothing about my wireless interface (which should be wlan0).
Then I downloaded a more recent (but stable) version of ndiswrapper form their website and everything went fine (dmesg prompts somthing about wlan0 then which means that the wireless is available).

Also to complie the source of ndiswrapper you have to install the kernel-headers from the CD (something like sudo apt-get install linux-kernel-headers-xxx-386).

Hope this will help a bit.

---

### Post by xsmind on 2005-11-13
I think this [topic]("http://ubuntuforums.org/showthread.php?t=85835") is about the same card. But people there suggest we remove prism54 drivers. I don't know how to do this though...

---

### Post by Lambert on 2005-11-13
If you run ```
lsmod
``` this shows you the modules that are loaded. 

To remove a module you type ```
sudo modprobe -r <module>
```

---

### Post by stevenyu on 2005-11-13
You might need to check whether there is already a kernel based module for your driver, if it does, you will need to remove it, otherwise your going to have two driver driving to use the hardware, which can cause this kind of issues.

---

### Post by xsmind on 2005-11-13
It seems working. I'll test it when there is access point nearby. Here is dmesg output:
```
 Unloaded prism54 driver
 ndiswrapper version 1.1 loaded (preempt=no,smp=no)
 ndiswrapper: driver prisma00 (Conexant,07/20/2004, 2.1.25.0) loaded
 ACPI: PCI Interrupt 0000:01:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
 ndiswrapper: using irq 11
 wlan0: ndiswrapper ethernet device ... using driver prisma00, configuration file ...
 wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
```
and iwconfig after that:
```

lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

```

It really seems the kernel loads wrong driver.

P.S. Oops I've forgot to say, thank you all for helping me stay away from windows.

---

