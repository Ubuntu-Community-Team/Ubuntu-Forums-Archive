---
title: "Dropped Packets"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by -Curtains- on 2008-05-22
Hey all,
I've just moved over from Kubuntu to Ubuntu Studio 7.10, I wasn't too keen on KDE in comparison to Gnome. So far I'm really enjoying it, it's already proven it's worth for uni work etc.

Getting down to the nitty gritty:
Everything works, except wireless is a little wierd. It seems to be dropping packets. It's one of those oh-so-problematic Broadcomm chipsets, running with the drivers suggested by the restricted drivers manager. 
Heres my ifconfig and iwconfig outputs after being connected for a while:

Iwconfig:
> lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"TheTelferFamily"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:19:E0:FA:A3:98   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level=-53 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:24355  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:14:A5:EA:AC:2F  
          inet addr:192.168.0.100  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:feea:ac2f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3900 errors:0 dropped:30781 overruns:0 frame:0
          TX packets:4654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4263170 (4.0 MB)  TX bytes:581834 (568.1 KB)
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8881 (8.6 KB)  TX bytes:8881 (8.6 KB)

I'm not sure what's going on here! Anyone know how I cna fix this?

---

### Post by prshah on 2008-05-22
> **-Curtains- said:**
> 
Everything works, except wireless is a little wierd. It seems to be dropping packets. 

Try turning off power management for the wireless device with```

sudo iwconfig eth0 power off
sudo iwconfig eth0 txpower fixed
sudo iwconfig eth0 commit
```

Either one of the first two commands may give an error; that just means that a particular mode is not supported. If _both_ commands give an error, sorry, no power management support. 

As for the third command: Some wireless chipsets require a "commit" command; those that don't will return a "not supported" error which can be ignored.

Also, I notice that you are running ipv6; do you actually have a ipv6 network? Usually most don't. In that case, you can add this line```
blacklist ipv6
``` to the bottom of your "/etc/modprobe.d/blacklist" file. To edit the blacklist file, use ```
sudo gedit /etc/modprobe.d/blacklist
```

Dont delete anything from that file, just add the line to the bottom of the file.

Any improvements?

---

### Post by -Curtains- on 2008-05-23
Noticeable - especially after blacklisting ipv6.

The power management option didn't seem to go so well though... my wireless seemed to turn of completely, I had to reboot a few times and fiddle with the hardware switch on the front to get it up and running again.

All seems a bit better now though. I'm still dropping packets though:
> eth0      Link encap:Ethernet  HWaddr 00:14:A5:EA:AC:2F  
          inet addr:192.168.0.100  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16808 errors:0 dropped:5144 overruns:0 frame:0
          TX packets:15396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23470914 (22.3 MB)  TX bytes:1319355 (1.2 MB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:890 (890.0 b)  TX bytes:890 (890.0 b)


I'm not sure if this is normal wireless behavior or if theres something still wrong... any further ideas?

---

### Post by -Curtains- on 2008-05-23
...and my Iwconfig, if it's needed:

> lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"TheTelferFamily"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:19:E0:FA:A3:98   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=85/100  Signal level=-49 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:16  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

