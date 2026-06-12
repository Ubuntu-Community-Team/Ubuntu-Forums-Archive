---
title: "Atheros Wifi Failure."
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by theDaveTheRave on 2008-05-15
Hi all,


Well I've had a strange problem, that I have now solved. I thought I would post details of it here in case any one else has a similar issue and finds the information here useful.

**The Story.**

I started up my laptop (Acer Aspire 3680) today and found that I had lost my Wifi network connection!

**What I tried.**

As far as I was concerned the interface was working on ath0, the icon in the bar said that this wasn't connected.

I opened the connection properties, and when I tried to "configure" the connection it couldn't be found?

so I then tried the following commands in the terminal.

*ls -C network*

Returned all the details for my various network cards, it showed my ahteros chip but it wasn't allocated any Logical Name - which was wierd?

*iwlist scan*

didn't show up any wifi links, just my loopback and ethernet.

*sudo ifup ath0*

probably a bit of a silly one to try as I knew there didn't seem to be an "ath0" interface, but it threw up a load of strange details, and the SIOCGFADDR error, which I didn't really uderstand,

So I thought maybe I need to bring the interface down before bringing it up... at least it made sense to me.... 
*sudo ifdown ath0*, and then back up  *sudo ifup ath0*

but again, no change.

so I decided to try to "roll back" any changes from the auto updates. The only problem is I don't know where to find what has been installed and when? I'm sure someone knows where this info is.... if they could post it here that would be great, so thanks in advance.

**The Solution.**

I opened up synaptic and searched for anything that had <atheros> in title or detail.

I simply removed all the programs and then re-installed just the one that tallied up with the kernel that I am currently running (available from the <hardware information> window... I can't remember the commande line for that detail.... can anyone help??..

**Reboot**

Problem solved, wireless working again, and I'm a happy bunny again!

Hope this has helped others.

Dave

---

### Post by packman1234 on 2008-05-15
Hi

I'm still having major issues for the last 2 weeks. My wireless is showing that I'm connected, but no internet. In ifconfig, it is showing ath0--IEEE 802.11g   ESSID:"" Nickname   Mode: Managed Access Point: Not Associated.
I keep fiddling around, and still cant get this to work right...Please Help- Its driving me INSANE!!!!

Bob:confused:

---

### Post by packman1234 on 2008-05-15
When I do lshw -C network,  its showing my wireless as wifi0.
Configuration: Broadcast=yes
driver=ath_pci
latency=0


I'll do whatever you suggest!!

Bob

---

### Post by theDaveTheRave on 2008-05-16
Packman1234.

There are lots of other threads out there where you should be able to get more "expert" help,

I just had this issue after one of the auto updates, and it annoyed me for about 4 hours..... madness really!

However, I will do what I can to assist.

put in the following commands into the terminal and cut an paste the output onto this thread.

these are the commands

<lshw -C network>
<iwlist scan>


here is the response that I get from the terminal, from these....

> 
davem@Dartagnon:~$ [COLOR="Magenta"]lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
[COLOR="Navy"]  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:16:36:c8:51:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes[/COLOR]
[COLOR="Red"]  *-network
       description: Wireless interface
       _[COLOR="Purple"]product: AR2413 802.11bg NIC[/COLOR]_
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       _[COLOR="Purple"]logical name: wifi0[/COLOR]_
       version: 01
       serial: 00:19:7d:40:b8:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.2.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g[/COLOR]
davem@Dartagnon:~$ [COLOR="Magenta"]iwlist scan[/COLOR]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

[COLOR="Navy"]ath0      Scan completed :
          Cell 01 - Address: 00:17:3F:15:5D:43
                    _[COLOR="purple"]ESSID:"Mousquetaires"[/COLOR]_
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-42 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
[/COLOR]
davem@Dartagnon:~$ 


I've highlighted certain parts, in the hope this may make things easier to understand....

commands are in [COLOR="Magenta"]magenta[/COLOR]

Important information is [COLOR="Purple"]_underlined in purple_[/COLOR]

I've tried to separate out various parts in different colours, [COLOR="Red"]red[/COLOR] and [COLOR="Navy"]blue[/COLOR]

from the <[COLOR="Magenta"]iwlist scan[/COLOR]> command you should get details of the interface that is being used for wifi access... if you can get one that supports scaning!

You'll possible notice that the logical name of the Atheros device is in fact _[COLOR="Red"][COLOR="Purple"]wifi0[/COLOR][/COLOR]_ - this is then split into a "vitual device" of ath0 as is seen on the return of the <[COLOR="Magenta"]iwlist scan[/COLOR]> command.

If you don't have a device that supports scaning, it means that your drivers may not be correct, or you may have a similar issue to mine, where they seemed to have loaded twice and were confilicting with one another.

Once you know what your device name is (my system uses the atheros product: AR2413 802.11bg NIC ) I would recomend that you use this as a search term on the forums.

you want to hunt down the madwifi drivers for your device. I'll give you all the help I can.

Please bear in mind however that although I have used Linux for a while, I am no "guru" in linux... I just prefer it to windows - mainly as it works with my belief in open source products.

anyway I hope that has helped.

Dave

ps. what system are you using?? also try searching for that.

---

