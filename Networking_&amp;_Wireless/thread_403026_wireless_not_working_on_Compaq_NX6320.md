---
title: "wireless not working on Compaq NX6320"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by Boots262 on 2007-04-06
Hi guys,

I just installed Ubuntu 6.10 and everything is working fine except my wireless.

I would love to post the results of an iwconfig and lshw, but I'm on my other (windows) box. :mad: So here's an abridged version.


When I run the command "sudo lshw -C network", I get the text DISABLED next to my wireless card entry (an Intel PRO/wireless 3945ABG card). That wireless card is called "eth1"


The laptop has a button that turns wireless on and off.

When I run "iwconfig" with the button ON, eth1 appears as "unassociated ESSID:off/any"

When I run "iwconfig" witht he button OFF, eth1 appears as "radio off ESSID:off/any"

Any help would be greatly appreciated. I really don't want to have to go back to windows, but this machine NEEDS wireless.

---

### Post by MeneM on 2007-04-06
Hi,

On these forums I found [this]("http://ubuntuforums.org/showthread.php?t=140085") post, and also this message on it:

> Finaly I got it working !

I was trying with a fresh installation from dapper flight 5 cd.
Apparently it has pbm with udev, because after updating it from the online repositories (and a reboot) it started to work immediatly ...
It also solved the fact that the system didn't see my flash memory when inserted....

Again, if anyone wants details, just ask !

The post has go lots more info though.

---

### Post by Boots262 on 2007-04-06
Hi,

thanks for the reply. I am using Edgy not Dapper, will this be a problem?

I am currently installing every available update through the Synaptic manager to make sure it's not that.

Otherwise, I'll ty this driver build, though this is the first time I've ever used Linux so I'm a little scared.

While I'm here, I'll post the proper results of an iwconfig and lshw:

lshw:

```
 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@08:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:be:62:dd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () link=no multicast=yes wireless=unassociated
       resources: iomemory:e8000000-e8000fff irq:169
```

iwconfig:

```
eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:462   Missed beacon:0
```

Does that make anything clearer?

EDIT: Actually, since lshw is already saying I have the ipw985 driver, it can't need that driver build, can it? How do I get rid of that huge "DISABLED"?

EDIT2: The problem is that in the System-Administration-Networkign box, the wireless card says "not configured" and won't scan available networks.

HOWEVER, when I input "iwlist eth1 scan", I get:

```
eth1      Scan completed :
          Cell 01 - Address: 00:18:4D:55:6C:CC
                    ESSID:"GRIFFITH"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-32 dBm  Noise level=-32 dBm
                    Extra: Last beacon: 0ms ago
```

So why the hell can't the networking control panel see it or connect to it? How do I get my card to scan?

---

### Post by Boots262 on 2007-04-06
OK, it seems to be working fine now (I'm using wireless as I type).

But I still don't quite understand how. The network control panel (found at System->Administration->Networking) was close to useless. When I clicked on Wireless connection, I coudl see no way to actually scan for available networks, but as soon as I went to terminal and typed in iwlist, it found griffith fine and then connected.

Now, I know this isn't windows, and I can't expect a nice little wizard for everythign - I'm more than comfortable usign the terminal.

But I want to understand what happened - I have to use this machine at uni, where there are a LOT of wireless networks and I need to be able to select which one I'm using. What terminal command should I use to do this?

---

