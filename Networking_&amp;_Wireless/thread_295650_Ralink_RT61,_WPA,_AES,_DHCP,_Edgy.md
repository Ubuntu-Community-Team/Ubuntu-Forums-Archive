---
title: "Ralink RT61, WPA, AES, DHCP, Edgy"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by Biozid on 2006-11-08
I have spent two days trying to get this card up and running with Edgy. Still no success. Has anyone managed to get this card working with WPA and DHCP? :-k 

I am using the latest CVS tarball downloaded from serialmonkey. Module loads fine.Here is the commands I used:

```
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=WPAPSK
sudo iwpriv ra0 set EncrypType=AES
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set WPAPSK=c655a8ee70243f77cd46b00b679c5c0ac31919f188b317e2a5927efb5264ca8c
sudo iwpriv ra0 set SSID=Whisky
```

This is where it fails:

```
sudo dhclient ra0
```

Output:

```
Listening on LPF/ra0/00:11:50:dc:c8:36
Sending on   LPF/ra0/00:11:50:dc:c8:36
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by neveceral on 2006-11-20
yes, try this HOWTO [http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

---

### Post by wieman01 on 2006-11-20
Try this howto if you are still interested...

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

BUT: I am not so sure if the native RT61 driver supports WPA2/AES. The native drivers lack behind the Windows drivers in terms of wireless security (authentication, encryption). If TKIP does the job for you, then fine. If not, try installing the card using "ndiswrapper" and the latest Windows driver from the vendor's website. 

Drop us a line if you need help.

---

