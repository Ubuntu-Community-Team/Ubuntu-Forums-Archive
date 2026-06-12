---
title: "Wireless settings lost on reboot"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by McHenry on 2006-07-19
I have my wireless connection up and running using ndiswrapper.

When I reboot my network connection is lost:
root@sales:~# iwconfig wlan0
wlan0     IEEE 802.11FH  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3
          RTS thr:2312 B   Fragment thr:2312 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I need to reenter:
iwconfig wlan0 essid ESSID
iwconfig wlan0 key open XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX
dhclient wlan0

Then the connection is up and running.

Surely there is a way to keep these settings so they do not need to be reentered every time...

Thanks in advance...
(ubuntu 6.06)

---

### Post by f_s on 2006-07-20
Hi there

sorry, no answer, just another one with the same problem. i figure it may have somthing to do with the interfaces file, like somthing missing there

regards

Frank

---

### Post by Titus A Duxass on 2006-07-20
f_s - you are correct. You need to edit the interfaces file.
You enter all your wireless details there and add auto wlan0 at the end.

---

### Post by McHenry on 2006-07-20
What's the file name and where's it located ?

Is there an example anywhere or is it relatively straight forward ?

---

### Post by Calamus on 2006-07-20
Find it at /etc/network/interfaces

sudo gedit /etc/network/interfaces

---

### Post by Eversmann on 2006-07-20
Another way is to use the network utility on System->Administration menu.

That utility writes the info on /etc/network/interface

---

