---
title: "RT61 wireless problems"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by Magpi on 2007-09-16
I have finally been able to make my edimax pci card work having read some instructions on the forum. This uses "iwpriv". I have to put the following lines in a terminal to make it work each time I turn on. Can anyone tell me where I can paste these lines so that it will boot up automatically? The tar file on the drivers disk from the linuxemporium constantly crashes out.

sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=FACADE6131
sudo iwpriv ra0 set SSID=SSD4TTX8
sudo dhclient ra0

I have also edited the "/etc/network/interfaces " file to contain the following:

iface ra0 inet dhcp
wireless-essid <my-essid>
wireless-key <my-key>
auto ra0

thanks for any advice. Please note I am a beginner!!!:lolflag:

---

### Post by kevdog on 2007-09-16
Great you already did the hard work yourself and figured things out.

Here is how you modify you /etc/network/interfaces file:

auto ra0
iface ra0 inet dhcp
     pre-up ifconfig ra0 up
     pre-up iwpriv ra0 essid "SSD4TTX8"
     pre-up iwpriv ra0 key FACADE6131


I think that should be it!

---

