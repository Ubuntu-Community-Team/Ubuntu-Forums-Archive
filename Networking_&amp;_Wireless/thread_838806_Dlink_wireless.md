---
title: "Dlink wireless"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by fewjr on 2008-06-23
Hi all,
     This is my first post here so please be patient.I have a Dlink DGL-510 which I don't seem to be able to connect to the internet with yet. I am using Ubuntu 8.04 Hardy Heron. lshw -C network shows:
     network0
     wireless interface
     AR2413 802.11bg NIC
     Atheros Comm Inc.
     logical name: wifi0
     configuration: broadcast=yes driver=ath_pci

     network1
     ethernet
     VT 6102 [Rhine-II]
     VIA Technologies, Inc.
     logical name: eth0
     configuration: broadcast=yes driver=via-rhine

All of the output from the network commands were done here at work without my home router nearby to connect with. I brought it to work to fool with it. When I had it at home and couldn't connect it showed the router in the gui but no internet.
     
     iwconfig shows:
     
     lo    no wireless extensions
     eth0  no wireless extensions
     wifi0 no wireless extensions
     ath0 IEEE 802.11g ESSID: "" Nickname ""

     I am typing these things so I am only putting in what I thought you might need to see for now. One question I have is since my wireless cards logical name is wifi0 and my ethernet interface on the motherboards logical name is eth0... what is ath0? If I run ifconfig it shows ath0 as having the same MAC address as wifi0. wifi0 is using irq19 while ath0 is using irq16.
     When I look at lsmods output I see these modules in the list. ipv6, ath_pci, wlan, ath_hal, via_rhine. Is it possible that I am having a conflict that is showing two instances of wireless interfaces,(ath0 and wifi0)? Or is ath0 supposed to be there.
     Also when I look at my interfaces file in the /etc/network/ directory it doesn't look anything like the sample I saw online. I used cat to read it and this is all it says:
     auto lo
     iface lo inet loopback
Maybe I used the wrong command to read it ...I'm new to this.
     I was going to try to use the madwifi driver, but maybe you all may be able to point me in the right direction. If you need more info I will be glad to comply. I am not online and I cannot get the madwifi tarball off of the dvd-r I burned it to. Apparently my dvdrom drive can only read cds in Ubuntu. Thats another issue I'm having. I guess one thing at a time. For some reason my windows box will not burn the tarball to a cd-r disk in nero but will burn it to a dvd-r. Go figure.
      Sorry for long winded post.
                                          Thanks
                                           fewjr

---

