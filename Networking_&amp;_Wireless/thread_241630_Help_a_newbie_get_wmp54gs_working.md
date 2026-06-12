---
title: "Help a newbie get wmp54gs working"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by edman2 on 2006-08-22
Ok so I just installed ubuntu, and for the most part I'm a complete newbie at linux. I've read a few things about installing the wireless card (linksys wireless g w/ speedboost wmp54gs), but they have been very confusing. Some say to use NdisWrapper some say to not etc...I don't even know where to start.

When I type in iwconfig I get the following:

lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr: off   Fragment thr: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


When I type in "lspci -v" i get this:

0000:00:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)
        Subsystem: Linksys: Unknown device 0015
        Flags: bus master, fast devsel, latency 32, IRQ 12
        Memory at ed000000 (32-bit, non-prefetchable) [size=8K]

Can someone point me in the direction I need to go (keeping in mind I know very little about linux).

---

### Post by Zed on 2006-09-03
Hi,

I have a WMP54GS working perfectly with 6.06 and ndiswrapper. I had basic networking functioning with bcm43xx, but ended up against something I couldn't do -- I don't remember what now (and I couldn't state absolutely that I was even right that bcm43xx was the problem) -- so I went back to ndiswrapper and have been happy with it.

Could you post the output of these commands, please?

```

lsmod|grep 'bcm\|ndis'
aptitude search bcm43 ndisw
cat /etc/network/interfaces

```

Setting up wireless networking with ndiswrapper is a small pain, but it's doable.

---

### Post by faraazs on 2006-09-09
I am trying to get my WMP54GS working as well. I tried those commands you posted and here is my output:

```
faraazs@desktop:~$ lsmod | grep 'bcm\|ndis'
ndiswrapper           177364  0
bcm43xx               124044  0
ieee80211softmac       29696  1 bcm43xx
ieee80211              37064  2 bcm43xx,ieee80211softmac
usbcore               130692  4 ndiswrapper,ehci_hcd,uhci_hcd
faraazs@desktop:~$ aptitude search bcm43 ndisw
p   bcm43xx-fwcutter                - Utility for extracting Broadcom 43xx firmwv   ndiswrapper-modules-1.8         -
p   ndiswrapper-source              - Source for the ndiswrapper linux kernel moi   ndiswrapper-utils               - Userspace utilities for ndiswrapper
faraazs@desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid linksys

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by Zed on 2006-09-15
Most people (myself included) seem to have better luck with ndiswrapper than bcm43xx.

Try the directions [here](http://www.ubuntuforums.org/showthread.php?t=25683).

---

