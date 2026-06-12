---
title: "setting up a wireless connection"
date: 2005-11-29
forum: Networking &amp; Wireless
---

### Post by spirou0711 on 2005-11-29
hi,

i'm making my first steps in linux, abd ubuntu doesn't detect my wireless card and my only possibility to connect to the web right now is wireless via windows. do you know where i can find the right package to activate my wireless in ubuntu and how i can install it, having the file saved in my windows partition? i have an 11a/b/g Wireless LAN Mini PCI Adapter Ethernet 802.3

thanks in advance for every advise!

christian

---

### Post by tomski on 2005-11-29
seeing as you are new to linux why dont you try plugging in a rj45 cable (network) to the access point (if it's a wireless dsl router) just to save your self a head ache..

im not being nasty, but i tried to set up a wireless card in linux and it was a nightmare from start and when i did get the thing up i had a weak signal !!!

i hope im not putting you off but personaly i would not try that at the moment as some drivers are hard to get and then when you get them you may need to compile them your self as i did.

try reading up on linux and get to know the os first then jump in....
linux is good but a majority of things are awkward or a bit fidly but it is a learning curve...

Then again if you are stubborn as i am then we could do with a name for the device because if it is really popular you may be in luck because others may have tried and got it to work and also can provide directions.

---

### Post by spirou0711 on 2005-11-29
thank you for your reply! unfortunately, i am not allowed to hardwire myself to the web (university rule). that's a little bit of a dead end, since i probably won't work a lot w/ linux w/o an internet connection and can't get connected via cable.
so maybe i should wait for some better drivers.

---

### Post by The Mekon on 2005-11-29
A good starting point is to bring up a terminal and type:

lspci

which should bring up something like:

brian@fonze-ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:08.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
brian@fonze-ubuntu:~$

In this case it tells us that I have an Ethernet controller using an Ahteros Communications chip which should just work wirh Breezy.

Check hadware compatabilty in the Wiki at:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

There is also some advice on Wireless networking set up on the Wiki.

---

### Post by spirou0711 on 2005-12-01
Alright, this is what I have:

0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)
0000:02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:01.0 Ethernet controller: Intel Corp. 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

However, despite the Atheros chip breezy doesn't seem to be able to configure it.
Any proposals?

---

### Post by Sendervictorius on 2005-12-01
Need a little more info. How do you know breezy hasn' configured it?  Are you comfortable using command line?

What is the output of ifconfig - to understand your network configuration? - and iwconfig - to understand your wireless configuration?

Do you have an ethernet as well? If so, have you disabled eth0 and enabled wlan0? 
  (ifconfig eth0 down
   ifconfig wlan0 up

If iwconfig worked ok, then try iwlist wlan0 scan to see if you can pick up an access point.

---

