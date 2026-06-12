---
title: "Regretfully having to use Windows 10"
date: 2017-12-18
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-12-18
Folks,

I've been an Ubuntu user for over 10 years now, for the last 7 years I've hardly touched Windows except at work.

Just over a year ago I bought a brand new Toshiba Satellite laptop which uses a Realtek WiFi chip and since I have not been able to use WiFi reliably.

I've followed advice on the forums, used some replacement Realtek drivers, tried ndiswrapper, all to no avail, it seems to work for about one or two minutes then web pages fail to load.

Under Windows 10 all works fine including the 5ghz connection but unusable in Ubuntu. Been making do with Ethernet but it is a laptop and is supposed to be portable.

This is my hardware and searches suggest it's been an ongoing problem with these popular wifi chips.

Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter

Geffers

---

### Post by ajgreeny on 2017-12-18
You don't say what you've tried other than "*I've followed advice on the forums*" which is not very helpful to us, but have a look at [https://ubuntuforums.org/showthread.php?t=2319956](https://ubuntuforums.org/showthread.php?t=2319956) where users seem to have solved the problem.

---

### Post by Geoff_Lane on 2017-12-22
> **ajgreeny said:**
> You don't say what you've tried other than "*I've followed advice on the forums*" which is not very helpful to us, but have a look at [https://ubuntuforums.org/showthread.php?t=2319956](https://ubuntuforums.org/showthread.php?t=2319956) where users seem to have solved the problem.

MAY HAVE RESOLVED THE PROBLEM

Main reason I didn't quote previous actions is because there have been so many things I've tried that it would be impossible to list - or difficult.

I actually tried Wicd as suggested in the link and disabling Network-Manager wicd found no wifi.

On one occasion after working for about 3 minutes I then got the rolling ball, all my wifi networks completely disappeared and did not return until reboot with the wifi option disappearing completely.

BUT - I appear to have resolved something, I've given my laptop a fixed IP and it seems to be working.

I have a number of fixed IP devices on my network but never really considered it on the laptop, well, fingers crossed, why a fixed IP should work and DHCP not I've no idea but one of the mysteries of computers and networks.

Geffers

---

