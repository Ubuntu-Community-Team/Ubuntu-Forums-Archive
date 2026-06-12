---
title: "Wireless doesn't start automatically at boot..."
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by elmerfud on 2007-03-17
I'm running an HP ZD7280 laptop with Kubuntu 6.10.  I really like it. 

I've got a little problem though.  The laptop has 2 ethernet devices, an ethernet card that connects with a regular ethernet cable and a wireless Broadcom 4306 card. 

Both of these devices work under edgy.  No problems there.   I've got the wireless card working with ndiswrapper. 

$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:0D:B5:59
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-71 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

The problem I have is that when I boot the laptop, it starts eth0, which is the ethernet card rather than eth1, which is the wireless device.  I can't get them to start both either.  To get my wireless ethernet working I have to do an ifup eth1 every time I boot.  I also do a ifdown eth0.  

My "network settings" in "system settings" shows eth0 to be disabled and eth1 to be enabled, but yet every time I boot eth0 comes up and eth1 doesn't. 

How do I fix this ?

Thanks.

---

### Post by chili555 on 2007-03-17
The key is, most likely in /etc/network/interfaces: To get eth1 to start automagically and eth0 to not, I suggest the file read like this: ```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid MYESSID
wireless-key <my_secret_key>
```You can sudo gedit the file.

eth0 does not include "auto ethX" but eth1 does. Yours may be reversed.

Reboot and let us know.

---

### Post by elmerfud on 2007-03-17
That fixed it !

My file had auto eth0 and but not auto eth1.   I removed auto eth0 because I don't want/need eth0 at boot.   I added auto eth1 and it works. 

Thanks for your help.

---

