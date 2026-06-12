---
title: "[SOLVED] Silan SC92031;Dynamic IP, Gutsy, Kubuntu"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by lost_poet on 2007-10-21
Although i see that kernel 2.6.21 supports the Silan sc92031 and Gutsy is on kernel 2.6.22, My Kubuntu Live CD did not detect my ethnet card - the infamous sc92031.

I am presently downloading Ubuntu. But will someone plz tell me if anyone has experienced successful auto loading of the said the ethernet card? I will post my progress once my ubuntu download finishes. But still, since the only difference in Kubuntu is the KDE instead of Gnome, would Ubuntu behave any differently?

My last experience with Feisty wasn't too good. Even after I used ndiswrapper and modprobe to install the winxp driver into Linux, I experienced frequent disconnections. It wasn't very useful so I had to uninstall it.

PS- My broadband connection has a dynamic IP, chages each time I connect.

---

### Post by noob12 on 2007-10-21
Can you please post what you get for
```

lspci -nn

```

---

### Post by lost_poet on 2007-10-21
okay, will do as soon as I can. Ubuntu is currently downloading...

---

### Post by lost_poet on 2007-10-21
hmmm...for some reason, the file I saved with the output of the command seems to be missing.

Here's what I saw - It recognised all my connected devices. It recosnized the Hangzhou card too. Although it then said - Unknown device. I will have to try again later.

Sorry...

---

### Post by lost_poet on 2007-10-22
okay, finally,  i got it!

> ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82815 Chipset Graphics Controller (CGC) [8086:1132] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 05)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 05)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 05)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 05)
01:09.0 Modem [0703]: PCTel Inc HSP56 MicroModem [134d:2189] (rev 04)
01:0b.0 Ethernet controller [0200]: Hangzhou Silan Microelectronics Co., Ltd. Unknown device [1904:2031] (rev 01)

---

### Post by lost_poet on 2007-10-22
OKAY! I am posting this using the live cd and so far so good.

What did was that I clicked on the network icon > manual config. > Wired Connection > static IP and gave in my details, correctly. 

Then. since I have PPPoE type connection, (ADSL), I used pppoeconf to set it up. Now tis pinging fine. But still the network Icon says *no network connections*. Could somone please tell me why is that?

Will it go away if I install it on to my system? The network moniter shows activity fine...

---

### Post by noob12 on 2007-10-22
OK. You might want to try a different thread for this with a title like "PPPOE and NetworkManager".  I don't know much about how NetworkManager works with ppp connections myself.

---

