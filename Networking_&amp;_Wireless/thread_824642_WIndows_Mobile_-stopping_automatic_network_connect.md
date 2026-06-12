---
title: "WIndows Mobile -stopping automatic network connection?"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by Mouth on 2008-06-10
No, this is not another Windows Mobile sync'ing question :)

I have Windows Mobile 6.1 on my phone/pda (HTC Hermes). I charge it by plugging it into the usb cradle that is attached to my laptop.

I run Ubuntu Hardy on the laptop, using wireless connection to my home router.

When I plug my Windows Mobile into the cradle for charge, Ubuntu on my laptop (nm-applet, NetworkManager applet on the panel) will automatically disconnect the wireless connection to my home router and make a wired network connection (using rndis) to my pda/phone.

I then have to click on nm-applet to change my network connection back to wireless via my home router to re-instate my network/internet connection.

How can I stop my networking from automatically connecting to the phone/pda wired connection when I plug it into its cradle?

Thanks.

---

### Post by chingadero on 2008-06-26
I am having the same problem on a wired network using a WM6 device.
This behavior just started recently for me (around upgrade to 2.6.24-19 kernel)
If you connect your laptop to your router via cable then plug your phone in, do you have the same problem?
It seems that Network Manager decides the WM6 connection is better than the LAN connection and switches over. In my case, it also erases all the entries in /etc/resolv.conf
I have submitted this bug for the network-manager package: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/242278](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/242278)
Any help would be appreciated.

---

### Post by chingadero on 2008-06-26
I added:
```
blacklist rndis_host
```
to /etc/modprobe.d/blacklist
and the problem stopped.

---

### Post by Mouth on 2008-06-30
> **chingadero said:**
> I added:
```
blacklist rndis_host
```
to /etc/modprobe.d/blacklist
and the problem stopped.


Legend!  Thanks heaps for the follow-up.

---

### Post by Mouth on 2008-07-19
Just following up on this topic ...

Hardy 8.04.1 (and Intrepid) have a better/cleaner solution for this problem, allowing you to sync your WM5 and WM6 (Windows Mobile) device with Hardy via SynCE with OpenSync. This solution also resolve gnome networking applet from taking preference and using WM5 or WM6 as your networkign device when you plug it in.

Refer: [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) (specifically the section about adding your device's interface to /etc/network/interfaces) and also [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192411](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192411) for the background details.

---

