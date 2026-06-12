---
title: "Wireless card that works out-of-the-box for Gutsy (7.10)"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by mjezell on 2007-12-27
I just wanted to pass along to anyone that is looking for a good wireless card supported out-of-the-box for 7.10 Gusty.  The price is right and for Gusty anyway it just works.

[COLOR="blue"]MSI PC60G IEEE 802.11b/g 32bit PCI2.2 Turbo G Wireless Adapter Up to 54Mbps Data Rates 64/128-bit WEP, WPA, WPA2, TKIP,AES,802.1x[/COLOR]
Link to newegg page - 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833158017](http://www.newegg.com/Product/Product.aspx?Item=N82E16833158017)

I'm running this on a older Intel system with a 1.6gig processor and 512mg memory loaded with Gutsy 7.10 running MythTV without a flaw.  Hope this helps anyone looking to spend that extra christmas cash.

---

### Post by daengbo on 2007-12-27
A lot of RaLink cards are having trouble in Gutsy with dropped connections. You're not having these issues?

For anyone who is having trouble, [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) has newer drivers which solve this issue.

---

### Post by Gina on 2007-12-28
I'm trying to get my number 2 desktop working with wireless - without any joy so far with Gutsy.  It has a Belkin PCI wireless card with RaLink RT2500 chipset.  This works fine with Feisty provided the interface is downed, then ESSID set with iwconfig, then upped again.  With Gutsy it doesn't work.

This PC is in a different room from the router and I currently have a 10m cable running round doorways and under carpets that I would dearly love to get rid of.  I use this PC as print server etc.  Printer is detected and works perfectly in Gutsy but not in Feisty.

This is what I get in Gutsy :-```
gina@old-desktop:~$ sudo iwconfig
[sudo] password for gina:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gina@old-desktop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
gina@old-desktop:~$ sudo iwconfig wlan0 essid mystery channel 11 
gina@old-desktop:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:15:8d:47
Sending on   LPF/wlan0/00:11:50:15:8d:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
gina@old-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"mystery"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gina@old-desktop:~$
```I'll check out serialmonkey

I might add...  I've used ndiswrapper in the past to get wireless working on my laptop - before the Broadcom chipset was directly supported and firmware easily installed.  Now, having had the RT2500 chipset working in Feisty I would prefer using a native Linux driver to ndiswrapper.  But if I can't get this to work I shall probably go back to trying ndiswrapper

---

### Post by Gina on 2007-12-28
Well ... I went to the serialmonkey site and downloaded **rt2500-1.1.0-b4.tar.gz** and followed the instructions but the **make** gives errors :(  Any suggestions, please?
```
gina@old-desktop:~/Desktop/rt2500-1.1.0-b4/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/gina/Desktop/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /home/gina/Desktop/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/home/gina/Desktop/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/home/gina/Desktop/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ‘RT2500_open’:
/home/gina/Desktop/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/home/gina/Desktop/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/gina/Desktop/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ‘rt2500_init_module’:
/home/gina/Desktop/rt2500-1.1.0-b4/Module/rtmp_main.c:1009: warning: implicit declaration of function ‘pci_module_init’
make[2]: *** [/home/gina/Desktop/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/gina/Desktop/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt2500.ko failed to build!
make: *** [module] Error 1
gina@old-desktop:~/Desktop/rt2500-1.1.0-b4/Module$ 

```

---

### Post by ::rml:: on 2007-12-28
Gina,

It looks like you might be having trouble compiling the new driver because you need what are known as "kernel headers." These should allow you to compile drivers for the linux kernel. I'd start by installing the package 'linux-headers-generic', e.g. 'sudo aptitude install linux-headers-generic'; if that doesn't work, there are other header files listed as well. Try 'apt-cache search linux-headers'.

I hope that helps you find what you need. I'll be really interested in how things work out for you with the new drivers, because I'm having the exact same problem myself. Good luck.

---

### Post by Gina on 2007-12-28
Thanks for your reply rml :)  meanwhile I downloaded and used the **CVS hourly tarball: rt2500-CVS** and had no errors.  I then tried setting essid with iwconfig but it wouldn't take so I tried the old trick of downing the interface.  THAT WORKED!!  (after rebooting) :):)

---

### Post by Gina on 2007-12-28
This is what I did :-
Copied the tarball to the Desktop
Then these commands :- ```
 cd Desktop
 tar -xvzf rt2500-cvs-daily.tar.gz
 cd rt2500-cvs-2007122808
 cd Module
 make
 sudo make install
 sudo ifdown wlan0
 sudo iwconfig wlan0 essid mystery channel 11 
 sudo ifup wlan0
```
After rebooting it needs :- ```
sudo ifdown wlan0
sudo iwconfig wlan0 essid mystery channel 11
sudo ifup wlan0
```
The result :-
```
gina@old-desktop:~$ sudo iwconfig
[sudo] password for gina:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2500 Wireless  ESSID:"mystery"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:6C:A8:DA:2A   
          Bit Rate=54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=84/100  Signal level:-59 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gina@old-desktop:~$
```

---

### Post by mjezell on 2008-01-07
The only thing that I do to get the card to work (I've been doing this since fiesty and it has always worked well ) is create a bash file in the /etc/init.d/ folder to restart the network at boot-up > #!/bin/bash
sudo  /etc/init.d/networking restartHope this helps.

---

### Post by ak-47 on 2008-04-05
been working on this card for a few hours,

finally got some "restricted" drivers that find the card - but still won't connect to my network.

I wouldn't consider this working "out of the box" - can't recommend this card.

---

### Post by ak-47 on 2008-04-06
don't buy this card

I've tried all suggested drivers and numerous how-tos

this card doesn't work, I'll be returning mine to newegg asap

hopefully I'll get lucky with the next one...

---

