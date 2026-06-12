---
title: "[SOLVED] [gutsy] KDE Network Applet not showing wireless networks"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by open_coder on 2007-11-20
Hello,

I installed Kubuntu 7.10 Gutsy Gibbon on an HP tc4200. For a while I was using the network manager that came with Kubuntu. It worked for a little bit. Unfortunately, the network manager isn't showing the wireless networks section any more. Is there any way to fix this problem?

Here is my iwconfig```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"<hidden>"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:153   Missed beacon:0

```

and my /etc/network/interfaces```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth1
iface eth1 inet dhcp

```

I think something might be missing from /etc/network/interfaces file. Can somebody post working samples of these files to help me out?

Thanks
OC

---

### Post by wieman01 on 2007-11-20
What wireless adapter have you got and what chipset is it? Please do...
> sudo iwlist scan
...and post the output.

---

### Post by open_coder on 2007-11-20
I know that the wireless adapter is an Intel/Pro Wireless adapter.

sudo iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:F8:3A:3D:69
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-50 dBm
                    Extra: Last beacon: 168ms ago

```

---

### Post by wieman01 on 2007-11-20
Please change "/etc/network/interfaces" so that it looks like this:
> auto lo
iface lo inet loopback
Then reboot the PC and see if you can connect.

---

### Post by open_coder on 2007-11-20
That fixed it. Thanks,

OC

---

### Post by wieman01 on 2007-11-20
Known bug. NM did that to me once as well. :-) See you around.

---

