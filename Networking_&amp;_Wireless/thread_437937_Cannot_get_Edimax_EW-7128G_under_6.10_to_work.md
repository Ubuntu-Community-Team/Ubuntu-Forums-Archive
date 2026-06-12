---
title: "Cannot get Edimax EW-7128G under 6.10 to work"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by tsu3000 on 2007-05-09
Hi

I cannot seem get WPA1 wireless working with the Edimax  EW-7128G PCI card (uses RaLink RT2561/RT61 chipset) under Ubuntu 6.10. After a fresh install I can see a wlan0 and wlanmaster0 in the network settings menu. I can enable the interfaces but they do not give options to use WPA1 or even WEP. Is wireless broken in a standard build for 6.10?

I have been through some tutorials on this forum eg [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) but this does not work on my setup. Maybe I am missing something?

Any help or pointers would be appreciated.

Thanks.

---

### Post by Skullster on 2007-07-10
Hi 

I am having the same problem myself.  I have tried this card on 7.04 but every time I try to configure it either in network manager or using system > networking the computer freezes up as the card is configuring.This happens on 2 different PCs.  I have tried Ndiswrapper and this also freezes 7.04! Maybe just this card?

On 6.10 I get the same cards detected and configuring either, neither or both does not work.  thought these worked "out of the box"?

---

### Post by peterl_j on 2007-07-10
Hi

I am trying to get it running under 7.04.  

I am having some problems, with /etc/network/interfaces (with the wireless stuff in in fell over) I
added auto ra0 iface ra0 inet dhcp to /etc/network/interfaces, and it then tries to work and
sudo iwlist ra0 scan gives me stuff including ESSID "Belkin54g, Mode
Managed, Channel 11, Encryption key on, Quality 0/100, signal level -30
dBm Noise level -256 dBm.

I then switched security off and Quality shot up to about 84/100.  Also Network Manager now "filled in " the bar for my belkin, but it still will not connect.

Peter

---

### Post by m_yates on 2007-08-03
I had a problem with this card under 7.04.  I tried a number of things and finally got it to work when I inserted the "rt61pci" module.  You could try the following:

```
ifdown ra0
modprobe rt61pci
ifup ra0
```

I also added "rt61pci" to /etc/modules so that the module is inserted on boot up.  "lsmod" shows that both rt61 and rt61pci are inserted.

In addition, I removed network-manager application, because I can't see what use it has.  I'm using WEP and I put the required parameters in /etc/network/interfaces:```
auto ra0
iface ra0 inet dhcp
wireless-essid abc
wireless-key 1234567...
```Where "abc" is my essid and "1234567..." is the WEP key.

Hope this helps you.  I've rebooted several times and it keeps working.  I was on the verge of ripping the card out of my PC and driving over it with my car.

---

### Post by peterl_j on 2007-08-04
Hi

Thanks for that.  I altered my interfaces as you did, except I used eth1.  I forget how I discovered this.

One problem however was that one then must not touch anything.  Though the applet looks wrong, leave it alone.  Mine shows I have a wired connection.

Thanks again, I think it was good value for £20!:)

Peter L-J

---

### Post by yogo on 2007-08-10
> **m_yates said:**
> I had a problem with this card under 7.04.  I tried a number of things and finally got it to work when I inserted the "rt61pci" module.  You could try the following:

```
ifdown ra0
modprobe rt61pci
ifup ra0
```

I also added "rt61pci" to /etc/modules so that the module is inserted on boot up.  "lsmod" shows that both rt61 and rt61pci are inserted.

In addition, I removed network-manager application, because I can't see what use it has.  I'm using WEP and I put the required parameters in /etc/network/interfaces:```
auto ra0
iface ra0 inet dhcp
wireless-essid abc
wireless-key 1234567...
```Where "abc" is my essid and "1234567..." is the WEP key.

Hope this helps you.  I've rebooted several times and it keeps working.  I was on the verge of ripping the card out of my PC and driving over it with my car.


My device is not configured, that is the response from terminal when I do a sudo ifdown ra0 How do I configure the card, it is seen through terminal and identified correctly but shows up unknown ra0 deveice in network tools.

Thanks

---

