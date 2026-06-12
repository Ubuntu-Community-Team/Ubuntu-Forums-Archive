---
title: "something with network manager"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by AxietY on 2007-02-01
i cant see enable wireless networking ,nor  my wireless networks when i left click on the network manager icon , the drivers are installed, can any1 help me solve this problem ? (A)

---

### Post by inCursorated on 2007-02-01
what type of adapter is it? run the iwconfig command and ensure it's recognized as a wireless device. you should see something like this in the output:
```
eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
if u see it, test it (the name may differ):
```
sudo ifconfig eth1 up
sudo iwlist eth1 scan
```
this should list the networks in range. 

i imagine it's working properly, you probably just have to use a different app just for wireless. On KDE, i use Wireless LAN Manager (wlassistant) and not the Network Settings applet.

---

### Post by empthollow on 2007-02-02
i had the same problem the other day.  i edited /etc/network/interfaces and commented out the interfaces i want network manager to use like such:
```
#auto ath0
#iface ath0 inet dhcp
#wireless-essid 

```
as soon as i restarted network-manager was working:guitar:

---

### Post by AxietY on 2007-02-02
It is already working ( i'm connecting from it ) , i ran "sudo iwlist eth2 scan" and it showed me the device and alot of other stuff,
so i'll try  #'em them out...

---

### Post by AxietY on 2007-02-02
thanks  all :)
seems that commenting things out works just fine :)

---

