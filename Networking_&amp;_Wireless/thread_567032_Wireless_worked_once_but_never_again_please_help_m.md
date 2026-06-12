---
title: "Wireless worked once but never again please help me!!!"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by shaneslinuxbox on 2007-10-04
Well I my new wireless cards came in and I plugged in the netgear worked out of the box no problems....so did the D-link but now I can't get wireless AT ALL I rebooted and wireless is gone. The DHCP seems to be working meaning it receive and IP but I cannot go out and use the interent at all I tried 2 different routers both cards and no luck nothing. I tired static IP I tried all I new to get it to work and still nothing. if someone can please help me I would surely appreciate it 

Shane

---

### Post by shaneslinuxbox on 2007-10-07
Well I found the best method to get my cards to work.....reload the OS nothing else worked now I sit here wirelessly filling this out. Both cards work well can exchange either one at either time but Im still trying to get WEP to come up with the netgear wg511t card. The only protection Im using atm is MAC address filtering not a perfect standard by far.  The netgear card has about 20% less range than the d-link 560 and costs more on average go with the D-link card big time. 

If any one can tell me how to get WEP to come up when I set it on my router with the netgear wg511t card please let me know 

Thanks,

Shane

---

### Post by hcorey on 2007-11-02
My Netgear WG511T stopped working on Gutsy--It seemed to connecting intermittendly and connected to Wep. However, over the past 2 days it has stopped working-no flashing lights, system log states cannot power PCMCIA. Has any on seen anything like this?

---

### Post by TsoTsalagi on 2007-11-03
Similar problems...here are the details:

Dell Inspiron 1100
Celeron processor (unfortunately)
BIOS rev A32
1GB RAM
Ubuntu Gutsy Gibbon v7.10 (not dual boot)
Netgear WG511T wireless card
Broadband ISP

Wired network (eth0) works fine.

Wireless card seems as if it is detected but is not connecting to Internet properly. Both lights on the card are blinking simultaneously, not alternately.

NOTE: I have not been able to install the OEM driver for the WG511T wireless card, because I haven't found a source for a non-windoze driver. Other threads in this wireless & networking forum indicate it should work "out of the box".

When I boot with the wireless card removed, the Wireless Connection does not display in System > Admin > Network.  If I insert the wireless card and re-start System > Admin > Network the Wireless Connection displays, and I think the Properties are entered correctly for my WEP connection (router provided by my ISP) but the device is ath0 (not wifi0).  I think this may be a problem, but not sure.

In System > Admin > Network Tools, on the Devices tab, if I choose the wifi0 network device, it displays "unknown interface (wifi0)", but the "Configure" button is alternately disabled and enabled at odd times.  When the button is enabled, if I click on it, a message pops up that says "The interface does not exist". But in the lower portion of that dialog box, the "Received Packets" and "Received Bytes" values are incrementing.

After reading an exhaustive number of user forums/threads, I cannot find any definitive solution and am thinking that wireless connections and/or this wireless card simply will not work with Gutsy Gibbon.  Would really appreciate if anyone can help.

Thanks!

---

### Post by TsoTsalagi on 2007-11-03
OK, after struggling (as a total noob) for several hours/days (actually a couple of weeks), I got wireless working (see specs in previous post) by running the command line scripts for WEP connections that are described in detail in another thread: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Thanks kevdog for the link in your signature!

However, I have not re-booted my laptop yet.  But I will report back shortly with the results.

---

### Post by TsoTsalagi on 2007-11-03
Alas...sorry to report that after re-starting my laptop, the wireless no longer connects to the Internet, so I'm back on the cable for now.  Still hoping for a permanent solution...thanks!

---

### Post by kevdog on 2007-11-03
Can you post

lshw -C network
iwlist scan

What doesnt exactly connect -- network manager, command line??

---

### Post by TsoTsalagi on 2007-11-05
lshw -C network:

```
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:b4:5e:26
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.0.13 latency=32 module=b44 multicast=yes
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:2f:e5:21:54
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

iwlist scan:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0E:9B:26:8A:56
                    ESSID:"45ae"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-36 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:0D:72:62:27:71
                    ESSID:" "
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
```

thanks for taking a look...hope you can help!

---

### Post by TsoTsalagi on 2007-11-05
Network Manager doesn't seem to work properly, but I'm trying to get Network Manager to work without having to add a different utility.  My wired connection is working, so wireless isn't critical...provides some time to struggle through this using 7.10 without customizing.

The command scripts you provided in the other thread worked only once, and haven't worked again after re-booting my laptop.

Thanks,
Tso

---

