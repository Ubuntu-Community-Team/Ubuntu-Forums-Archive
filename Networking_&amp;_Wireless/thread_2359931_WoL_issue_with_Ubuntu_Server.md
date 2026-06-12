---
title: "WoL issue with Ubuntu Server"
date: 2017-04-29
forum: Networking &amp; Wireless
---

### Post by jfreeks on 2017-04-29
Normally I don't post to forums, but I'm all out of ideas for this problem and would greatly appreciate any help. I'm trying to enable wake-on-lan on a machine running Ubuntu Server 16.04.2 LTS. Basically, it doesn't work.
ethtool shows "Wake-on: g" for the network card in question. If I send a wakeonlan command to the server from the router (or another machine in the same LAN) while tcpdump or tshark is running on the server, the server doesn't show any indication of receiving the packet. At the same time, other machines on the network do receive the packet, so it is actually being sent. Normally, this wouldn't strike me as being an unusual problem, but if I change the MAC address used in the wakeonlan command to something that isn't the MAC address of the server (e.g. the MAC address of another machine on the LAN, or just a bogus MAC address), then tcpdump and tshark both receive the packet. (Obviously it couldn't wake up the machine due to the MAC address mismatch.) So, in summary, its only receiving (or acknowledging) magic packets when the MAC address isn't its own. Linux isn't my forte, but this seems like odd behavior to me. Anybody know how I should proceed with this problem? Thanks.

P.S. I should probably mention that I'm using a troublesome JMC250 network card. During install of Ubuntu Server, the install didn't recognize the network card. After install all I had to do was manually enter the network card into /etc/network/interfaces and it started working just fine. The internet seems to indicate that Ubuntu users have had bigger problems with this network card in the past, so I figured it would be good to mention at least.

---

### Post by litlesam on 2017-04-29
Been so long since doing it myself. Worked rather easily using these 3 threads.
[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)
[https://askubuntu.com/questions/774404/how-can-i-enable-wol-on-ubuntu-server-16-04](https://askubuntu.com/questions/774404/how-can-i-enable-wol-on-ubuntu-server-16-04)
[https://www.cyberciti.biz/faq/ubuntu-linux-wake-on-lan-client-command-installation-examples/](https://www.cyberciti.biz/faq/ubuntu-linux-wake-on-lan-client-command-installation-examples/)

---

### Post by papibe on 2017-04-29
Hi jfreeks, welcome to the forum ):P

Did you enable WOL on the BIOS? (sometimes also called "PCI Power up", "Allow PCI wake up event", "Boot from PCI/PCI-E", etc).

When it is enabled, you'll see the typical ethernet leds light up, even if the machine is poweroff. 

Just a thought. Let us know how it goes.
Regards.

---

### Post by jfreeks on 2017-04-29
Ah, I forgot to mention this issue. Oddly the BIOS has no indication of WoL, in any variation of the name. I've implemented WoL a few times over the years on various machines, and they've always had some version of WoL buried somewhere in the BIOS, but this one has been the exception. (It seems like any machine made in the past decade has the option in the BIOS, so I found it odd that I couldn't find it.) I was just crossing my fingers and hoping it would still work. I didn't think the lack of BIOS setting would cause the odd output seen in tcpdump/tshark. I figured the machine would still at least see the signal, just maybe not wake up to it if the BIOS didn't support it.

I know people tend to miss BIOS options when looking for them, so for your peace of mind, I'm listing all the BIOS tabs below so you know I didn't just miss it, with their various options (minus the 'Save & Exit' tab):

ADVANCED -> [Start Easy Flash] [ASUS FancyStart] [POST Logo Type] [Play POST Sound] [Internal Pointing Device] [Intel Virtualization Technology] [VT-d] [Legacy USB Support] [SATA Configuration]

BOOT -> [UEFI Boot] [PXE ROM] [Boot Option Priorities] [Hard Drive BBS Priorities] [CD/DVD ROM Drive BBS Priorities] [Network Device BBS Priorities] [Delete Boot Option]

SECURITY -> [User Password] [I/O Interface Security]

Ah, almost forgot to mention, unfortunately this machine doesn't have ethernet LEDs to indicate its state, but on the other end of the ethernet cable (connected to the router) the lights indicate green (for connected) and the occasional orange blink (for activity) when in a sleeping state. When the machine is completely off, there are no lights.

---

### Post by papibe on 2017-04-29
> **jfreeks said:**
> When the machine is completely off, there are no lights.
Not very promising :(

Have you take a look at [this]("https://help.ubuntu.com/community/WakeOnLan") tutorial?

Please get the name of your interface from this command:
```
ip link
```
and then run this command and post back the output (you can copy/paste the text from the terminal).
```
sudo ethtool enp2s0
```
(replace enp2s0 with your actual NIC name).

Regards.

---

### Post by jfreeks on 2017-04-30
I hadn't looked at that particular tutorial, but I looked it over and confirmed that I've already done the things they recommend. The only thing I can't do that the tutorial says to do is change the BIOS setting, as previously mentioned. I'm still confused as to why the missing BIOS setting would cause the magic packet to not be received at all, even when the computer is awake, but certainly anything is possible at this point.

Per your request, I'm posting the output of those commands. I've changed my actual NIC name and MAC address to bogus ones, to be safe.

"ip link" generates this: (we only care about enp2s0)
```

[SIZE=2]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 39:d5:52:c5:97:54 brd ff:ff:ff:ff:ff:ff
3: wls1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 35:d1:83:1c:b8:34 brd ff:ff:ff:ff:ff:ff[/SIZE]

```

"sudo ethtool enp2s0" generates this:
```

[SIZE=2]Settings for enp2s0:
    Supported ports: [ TP MII ]
    Supported link modes:    10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:    10baseT/Half 10baseT/Full 
                              100baseT/Half 100baseT/Full 
                              1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes: 10baseT/Half 10baseT/Full 
                                        100baseT/Half 100baseT/Full 
                                        1000baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x000020c6 (8390)
                    probe link rx_err tx_err hw
    Link detected: yes[/SIZE]

```

---

### Post by papibe on 2017-04-30
Thanks.

The software part looks OK.

Both the motherboard, and the card have to support WOL in order for this to work. If there's no mention on the BIOS, may be the motherboard does not support it after all..

I wonder if you could open your machine and take note of the motherboard brand and model to see if there's documentation about the it.

Regards.

---

### Post by jfreeks on 2017-04-30
Looked everywhere, unfortunately there's no documentation online for this motherboard. I find it odd that the BIOS supports something as strange as PXE but not something common like WoL. Even the manual for the machine itself mentions:
> ...certain wake-up components like LAN needs to remain powered. as if the network card is a wake-up component. Of course, that same phrase appears in manuals for different models, so they could have just copy-pasted it without checking if this machine actually supported it. Well, for now I'll keep searching around for a solution.

---

