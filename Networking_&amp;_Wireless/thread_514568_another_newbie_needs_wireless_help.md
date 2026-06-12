---
title: "another newbie needs wireless help"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by rs1996 on 2007-07-31
I am a complete newbie with Linux. I recently had Ubuntu installed on my laptop and working but had to reimage the PC due to some hardware failures. I have it back and Ubuntu 7.04 running but I cannot get the wireless to work like I did before. Also how can I change the card to work in 802.11b mode? I have searched the forums for assistance but can't seem to get it.
[B]
iwconfig:[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.7 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions

**sudo iwlist ath0 scan:**
ath0      Scan completed :
          Cell 01 - Address: 00:14:BF:CE:AB:46
                    ESSID:"XXXXXX"  (where XXXXXX is the actual SSID of my router)
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

---

### Post by noob12 on 2007-07-31
It would be helpful if you post information about your hardware

```

lspci -nn
lshw -C network

```

The card should associate to that access point in the current mode.  The access point seems to be a 802.11b/g.  Are you sure you want to restrict it to 802.11b?

Based on this page: [http://www.fehu.org/atheros-en.html](http://www.fehu.org/atheros-en.html)

I'd suggest this if you really want to restrict it to b mode.
```

sudo iwpriv ath0 mode 2

```

---

### Post by rs1996 on 2007-08-01
Hardware info for the wireless

02:02.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5211 802.11ab NIC [168c:0012] (rev 01)

<><><><><><><>

  *-network:0             
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:4e:40:d1:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.102 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:c0200000-c020ffff irq:11

---

### Post by noob12 on 2007-08-01
Did you get it working then?  I notice in your latest output you show a configured ip address and 802.11b mode.

> 
configuration: broadcast=yes driver=ath_pci [COLOR="DarkGreen"]ip=192.168.1.102[/COLOR] latency=168 maxlatency=28 mingnt=10 multicast=yes [COLOR="DarkGreen"]wireless=IEEE 802.11b[/COLOR] resources: iomemory:c0200000-c020ffff irq:11


This makes it look like you have associated to the access point and have been assigned an ip address.

If you are still having problems, what's not working?  Can you describe what you do and what you're having problems with?

Also, in the case you need more help, can you also show the result of
```

ifconfig -a

```
and (again)
```

iwconfig ath0

```
because the situation seems to be different now.

---

### Post by rs1996 on 2007-08-01
Yes...it seems to be working now. All I did really was changed the mode to 802.11b from .11a >> does that make sense?

I wanted to set it to .11b b/c my wireless card is fairly old and does not support .11g

So far so good...I will put it to the test a bit more later today and post back if I still have problems.

Thanks for your help so far...

---

### Post by noob12 on 2007-08-01
Thanks.   Normally, in this situation with an a/b card and a b/g AP, I'd expect the driver to associate to the router in b mode automatically. If you had to force the card into b mode with the **iwpriv** command I suggested, that's a useful thing to know.

EDIT:  Also, if you want help setting the command to run automatically, let me know.

---

### Post by rs1996 on 2007-08-01
Everytime I ran iwconfig, it would show the card as .11a. I knew there was a command to change the mode but did not have any idea what it was.

I have restarted just to see what would happen and it still works, showing the mode to be .11b

I even downloaded a truckload of OS updates on the wireless.

How do you run the command automatically?

So far so good...

---

### Post by noob12 on 2007-08-01
Great!

If things keep working automatically I would not add any script at all.  If you find you frequently need to type the command in order to associate to b/g access points, then the following instructions will set up a script to do this automatically before the interface is brought up.

```

% cd /etc/network/if-pre-up.d
% xhost +
% sudo gedit setwifimode

```

Put the following script contents into the file exactly as shown here.  I've used the logical name
**wifi0** for the interface based on your last output.  If you use a different one, change the MY_WIFI setting in the script.

```

#!/bin/sh

MY_WIFI="wifi0"
if [ "$IFACE" = "$MY_WIFI" ]; then
    iwpriv $IFACE mode 2 
fi

```

Save the file and exit.  Make it executable

```

% sudo chmod +x setwifimode

```

Note: this works even with the interface in "roaming mode" managed by NetworkManager.

Let me know if you need more help.

---

