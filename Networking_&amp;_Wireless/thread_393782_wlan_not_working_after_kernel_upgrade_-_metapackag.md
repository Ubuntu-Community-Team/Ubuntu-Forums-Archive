---
title: "wlan not working after kernel upgrade - metapackage f. restricted modules installed"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by hanzz on 2007-03-26
hi together,

as far as I know the package "restricted modules" is required to get a WLAN up and working in Ubuntu. Additionally, it is required to install the "restricted modules" metapackage so that the package is automatically updated when a kernel upgrade occurs.

Now I installed 6.10 edgy some weeks ago and my wlan worked out of the box. the metapackage for restricted modules is installed. After a kernel upgrade from 2.6.17-10 to -11 WLAN did not work any more.

What could be the problem in that case? 

hanzz

---

### Post by mahy on 2007-03-26
what's your wifi adapter?

Are you sure you've got exactly *this* package installed: linux-restricted-modules-2.6.17-11-generic ?

---

### Post by hanzz on 2007-03-26
lspci says:

00:0b.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01) 

and I have installed both restricted modules packages:

linux-restricted-modules-2.6.17-11-generic
AND
linux-restricted-modules-2.6.17-10-generic

I think this is because I have installed the correct metapackage so that the specific package
for each kernel version is installed automatically.

So why is kernel ...-10 bringing up the wlan card and ..-11 is NOT?   Does anything else need to be maintained after a kernel upgrade ?

hanzz

---

### Post by mahy on 2007-03-26
No idea. What does 'iwconfig' show you?

---

### Post by domzo on 2007-03-26
A lot of people have had this problem.

I just resolved it by removing the new kernel. (Well there was nothing wrong with the old  one :) ) But that's obviously treating the symptoms rather than the cause.

Anyway if you search recent threads someone might have got to the bottom of this by now.

---

### Post by hanzz on 2007-03-26
this is what iwconfig says (I masked essig and mac address with some xxx):
==

krnl 2.6.17-10
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"xxxxxxxxx"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:xxx:xxx:xxx    
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/92  Signal level=-45 dBm  Noise level=-140 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

krnl 2.6.17-11
lo        no wireless extensions.

wlan0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

