---
title: "help setting up wireless connection"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by cpeters12 on 2008-07-02
I have ubuntu 8.04 (hardy)
I am trying to connect to a local network i have set up.  The computer running ubuntu will be connecting wirelessly to a home network using a netgear ma101.  The home network is working off of a computer running microsoft xp and using a D-Link DI-713P.  To my knowledge the network is running fine.  I am just having trouble connecting my ubuntu computer to it. 


and i have spent hours and hours searching many different forums to try and figure out what to do.  I have found that people have successfully configured their systems to work with this particular wireless device (netgear ma101).

My question:  If you could please help me set this up with easy instructions.  I wouldn't consider myself a newbie to linux, only a newbie to the internet stuff.  Thanks.

---

### Post by superprash2003 on 2008-07-02
firstly to see if your ubuntu has successfully recognized your card, go to the terminal and type iwconfig and post output here

---

### Post by cpeters12 on 2008-07-02
> **superprash2003 said:**
> firstly to see if your ubuntu has successfully recognized your card, go to the terminal and type iwconfig and post output here

lo      no wireless extensions.

wlan0   IEEE 802.11b  ESSID:"linksys"  Nickname:""
        Mode:Managed Frequency:2.437 GHz Access Point: 00:13:10:9C:28:D6
        Bit Rate:11 Mb/s  Tx-Power+15 dBm
        Retry limit:8  RTS thr=1536 B  Fragment thr=1536 B
        Power Management:off
        Link Quality:0 Signal level:0 Noise level:0
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0  Missed beacon:0

---

### Post by cpeters12 on 2008-07-02
i also entered: lsusb
Bus 002 Device 003: ID 0864:4100 NetGear, Inc. MA101 802.11b Adapter

---

### Post by superprash2003 on 2008-07-03
ok.. it shows the linksys network.. on the top right hand corner you should see a network symbol(two monitors).. when you click on it, dont you see the available wifi networks(linksys in this case)

---

### Post by cpeters12 on 2008-07-03
I think I don't have my wireless network configured correctly on my windows machine.  Thanks for the help.

---

