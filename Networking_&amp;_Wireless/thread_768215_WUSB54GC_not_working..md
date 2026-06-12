---
title: "WUSB54GC not working."
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Sportingfan on 2008-04-26
Hi all,

as you may understand from this thread's title, i'm willing to connect to the internet using a linksys WUSB54gc usb adapter.

I know this forum is full of how-to's about this specific adapter, but i started a new thread.

I followed [this how-to ]("http://ubuntuforums.org/showthread.php?t=400236").
Everything went fine untill step 13 and 14.
When i do:
```
ifconfig -a
```
The output from this command is:

```
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:B5:75:C6  
          inet addr:81.82.59.30  Bcast:255.255.255.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7407006 (7.0 MB)  TX bytes:586741 (572.9 KB)
          Interrupt:11 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5248 (5.1 KB)  TX bytes:5248 (5.1 KB)

rausb0    Link encap:Ethernet  HWaddr 00:1D:7E:11:73:8D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:272902 (266.5 KB)  TX bytes:908840 (887.5 KB)

rausb0:av Link encap:Ethernet  HWaddr 00:1D:7E:11:73:8D  
          inet addr:169.254.5.218  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
```

As you can see, there is no wlan0 or whatever in this list.
I ended up with the rausb0 after following [this how-to]("http://wiki.archlinux.org/index.php/RT73_Wireless") earlier on. This how-to also went fine untill the "install firmware section" 
When i tried 
```
cp rt73sta.dat /etc/Wireless/RT73STA
```
the directory /etc/Wireless/ did not exist.

Any help? Suggestions?

Thx

---

### Post by HunterThomson on 2008-04-26
Not a problem I have one. It is not listed as Wlan0 it is called rausb0 that is fine.

then do iwconfig rausb0 up

---

### Post by HunterThomson on 2008-04-26
You should install this driver instead it can be put into "monitor mode" and you can do "paket injection"

[http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-2.0.1.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-2.0.1.tar.bz2)

also watch this video It shows you how to install the driver and use it...

[http://infinityexists.com/2008/03/08/episode-16-wireless-hacking-cracking-wpa/](http://infinityexists.com/2008/03/08/episode-16-wireless-hacking-cracking-wpa/)

---

### Post by Sportingfan on 2008-04-26
> **HunterThomson said:**
> You should install this driver instead it can be put into "monitor mode" and you can do "paket injection"

This works untill:
```
sudo make install
```
It returns:
```
grep: /etc/modprobe.conf: Directory or file does not exist.
```

Any other suggestions?

Thy

---

### Post by Sportingfan on 2008-04-26
I also tried this: [http://ubuntuforums.org/showthread.php?t=564419]("http://ubuntuforums.org/showthread.php?t=564419")

It ended with these messages (all other did not have errors or..)

```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "mykey".
*       Running dhclient..
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/rausb0/00:1d:7e:11:73:8d
Sending on   LPF/rausb0/00:1d:7e:11:73:8d
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
*               Script complete, You should now be able to connect, if not - Read the FAQ.
```

It seems that is does not take my psk.

?

---

### Post by HunterThomson on 2008-04-26
Well, I followed the method described on Full Disclosure. It worked for me in Backtarck3 and it worked in Ubuntu. I would install it gain to work out exactly what I did but when I did it last time in Ubuntu it messed up the drivers for my built in wireless card.

With that said, I would suggest working out the driver that was written for Linux and not do the ndiswrapper thing. 

Try looking through your file system for the file.

whereis modprobe.conf

I think this video had a better description of how to install the drivers

[http://infinityexists.com/2007/06/14/episode-3-wireless-hacking-deauth/](http://infinityexists.com/2007/06/14/episode-3-wireless-hacking-deauth/)

---

### Post by Sportingfan on 2008-04-29
I found modprobe.conf, but that didden't do it. After the 'make install', still no connection.
> 
I think this video had a better description of how to install the drivers

[http://infinityexists.com/2007/06/14...acking-deauth/](http://infinityexists.com/2007/06/14...acking-deauth/)
What should this video tell me? How to crack wep?

Any further suggestions?

Ty

---

