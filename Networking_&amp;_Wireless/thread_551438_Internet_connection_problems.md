---
title: "Internet connection problems"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by dnccnd on 2007-09-15
I'm having problems with my network connection. I have an ADSL modem that is also wireless. The setting of the wireless connection have been changed by the provider and therefore I cannot use it anymore, neither from my Windows partition. But while in Windows the LAN connection works, in ubuntu it doesn't anymore, and I really don't understand why. It used to work fine! I recently made a major update on the ubuntu system as I hadn't used my pc for a while. I guess something has messed up my network settings. This means that I cannot use Skype either and other online tools.

I have just had some problems with the sudo command too after the major update and managed to solve it by retyping the correct content of /etc/hosts. Therefore I think the update has messed some things up!

Can anyone help solve this problem?

---

### Post by ofri on 2007-09-15
did you try disabling ipv6 as explained [here]("http://www.linuxquestions.org/questions/showthread.php?t=326645") and [here]("http://ubuntu-tutorials.com/2006/10/20/how-to-speed-up-firefox-or-flock-ubuntu-606-610/")?


if that doesn't work, you might want to post some outputs here:
```
lspci -nn

sudo lshw -C network

sudo ethtool eth0

sudo ethtool eth1

dmesg
```

---

### Post by dnccnd on 2007-09-16
I looked at the posts you gave me, but I didn't manage to do much, they also refer to internet connection boing too slow, while mine doesn't work at all.

This is what I get with the commands you gave me:

mauro@ubuntu:~$ lspci -nn
0000:00:00.0 0600: 8086:3575 (rev 02)
0000:00:01.0 0604: 8086:3576 (rev 02)
0000:00:1d.0 0c03: 8086:2482 (rev 01)
0000:00:1d.1 0c03: 8086:2484 (rev 01)
0000:00:1d.2 0c03: 8086:2487 (rev 01)
0000:00:1e.0 0604: 8086:2448 (rev 41)
0000:00:1f.0 0601: 8086:248c (rev 01)
0000:00:1f.1 0101: 8086:248a (rev 01)
0000:00:1f.3 0c05: 8086:2483 (rev 01)
0000:00:1f.5 0401: 8086:2485 (rev 01)
0000:00:1f.6 0703: 8086:2486 (rev 01)
0000:01:00.0 0300: 5333:8c2e (rev 05)
0000:02:00.0 0607: 104c:ac51
0000:02:00.1 0607: 104c:ac51
0000:02:02.0 0280: 1260:3873 (rev 01)
0000:02:08.0 0200: 8086:1031 (rev 41)
mauro@ubuntu:~$ sudo lshw -C network
Password:
  *-network:0 DISABLED
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 01
       serial: 00:20:e0:8a:3c:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmwar e=Intersil 1.3.3 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:ec000000-ec000fff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth1
       version: 41
       serial: 00:d0:59:a8:ae:66
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1 00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion =3.4.14-k4-NAPI duplex=full firmware=N/A ip=192.168.1.100 link=yes multicast=yes  port=MII speed=100MB/s
       resources: iomemory:c0200000-c0200fff ioport:7000-703f irq:11
mauro@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
        Link detected: no
mauro@ubuntu:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
mauro@ubuntu:~$ 

Does this tells you anything?

Thank you for your help!

---

### Post by ofri on 2007-09-16
ok. did you try [this]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html")?

---

### Post by dnccnd on 2007-09-18
Yes, I have tried and changed the settings to see whether it would work.

Here are some shots of the networking panels. Starngely, I cannot set the default getaway device to eth1, that is to say the ethernet connection (neither can I set it to eth0, wireless).

---

### Post by dnccnd on 2007-09-20
Is there anybody who can take over and help me solve this problem?

Thanks!

---

