---
title: "WiFi looks fine -- won't connect."
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by rcoconnell on 2008-06-14
I have an oldish RamLine "tablet" running Xubuntu Edgy (2.6.17-12 kernel).  In the PCMCIA slot I have a Spectrum24 wireless card.  This was working awhile back, but doesn't seem to work any more.  I've been managing the card through the "NetworkManager" applet, not through "Network Settings".  It no longer lists any networks as being available.  I've been able to manually enter the SSID for my network and connect once today -- that gave me zero signal strength, and on all of my other attempts I've simply failed to connect.  I'm not sure what other diagnostics to run to figure out the problem!

This is old hardware, so I started by running 

```

$pccardctl status
Socket 0:
  no card
Socket 1:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "orinoco_cs"

```

Good, it looks like the PCMCIA slot still works and the wireless card is at least able to identify itself.  I then ran

```

$iwconfig
lo             no wireless extensions.

eth0           IEEE 802.11-DS ESSID:"" Nickname:"Prism I"
               Mode: Managed  Bit Rate: 11 Mb/s
               RTS thr: off
               Link Quality: 0  Signal level: 0  Noise level: 0
               Rx invalid nwid:0 iinvalid crypt: 0  invalid misc:0

sit 0           no wireless extsneions.

```

I tried following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=684495"), and ran into trouble on step three:

```

$sudo ifconfig eth0 up
SIOCSIFFLAGS: Device or resource busy

```

I think this is a problem.  I soldiered on, since the iwconfig stuff ran without complaint, but at the end got

```

$sudo dhclient eth0
SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth0/(MAC ID here)
Sending on LPF/eth0/(MAC ID here)
Sending on Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
No DHCPOFFERS received
No working leases in persistent database - sleeping.

```

I'm not sure what to do here.  I'm hoping this is a configuration problem, since mucking about with the software is hard (no ethernet port, no cd drive).  Any thoughts?

-ross

---

### Post by chili555 on 2008-06-14
This is what I did to get my ancient Prism to connect perfectly. *sudo gedit /etc/pcmcia/config.opts*. Substitute your favorite text editor here, such as kwrite, nano or vim. Add a new line:```
exclude irq 3
```Proofread, save and close gedit. Reboot. Does your wireless work now?

---

### Post by rcoconnell on 2008-06-15
Thanks for the suggestion!  I gave it a try, but alas, no joy.

I should add that the wireless card works fine under Win98.

-ross

---

### Post by chili555 on 2008-06-16
I just read this: [http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=562](http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=562)

---

### Post by GenesisV2.0 on 2008-06-16
If it worked in Dows98 download the drivers from the producer and ndis wrapper it, usually works if you can figure out the rubix cube that is Ndiswrapper. i have had similar problems with windows wireless cards that say they work on linux so give it a try and tell me if it works cause i found Ndis really hard but worth it

Hope i helped

---

### Post by rcoconnell on 2008-06-18
Hm.  My BIOS doesn't have any options like that.  It's pretty old (ca. 2000).

---

### Post by rcoconnell on 2008-06-18
Thanks for the suggestion, I may try that next.  I've also asked for help from [orinoco-users]("http://sourceforge.net/mailarchive/forum.php?thread_name=4855E645.7030706%40charter.net&forum_name=orinoco-users"), so that's another avenue I'll be pursuing.

-ross

---

