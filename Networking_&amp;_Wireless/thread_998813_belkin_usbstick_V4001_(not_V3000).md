---
title: "belkin usbstick V4001 (not V3000)"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by ryry46d9 on 2008-12-01
so I have bin looking all over the place trying to understand why my V4001 is only connecting at 24Mb with no luck

It seems all the forms out their are for the V3000s, does any one have any updated info for me , I would like a little more bandwidth on my lan

im going to leave out a few things from HOWTO post a Wireless issue (ticket)

due to the fact they are not needed 


but info I did find :


zd1211rw

A large proportion of USB-wireless devices on the consumer market are based on the ZyDAS ZD1211. Several months after the acquisition, Atheros rebranded the chip to AR5007UG.

zd1211rw is a community effort to rewrite ZyDAS's ZD1211 driver. zd1211rw has been included in the kernel since Linux 2.6.18. 

( ok   Linux 2 6 18 Released 20 September, 2006 )

if you go to the belkin site its all about windows 


lsusb:
Bus 005 Device 004: ID 050d:705c Belkin Components 

lsmod:
ieee80211softmac       30976  1 zd1211rw

ieee80211              35528  2 zd1211rw,ieee80211softmac

usbcore               146412 7 zd1211rw,sn9c102,gspca,usbhid,ehci_hcd,uhci_hcd

lshw -C network:
*-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: blanked out by me 
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.99 multicast=yes wireless=IEEE 802.11b/g

lsb_release -d:
Description:	Ubuntu 8.04.1

uname -mr:
2.6.24-22-generic i686



hope this info is enough , Like I said it works I would just like to get the full speed out of it

---

