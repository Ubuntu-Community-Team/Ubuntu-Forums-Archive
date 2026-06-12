---
title: "wireless not picking up settings correctly after reboot???"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by callagga on 2008-04-29
Hi,

I've just installed MythBuntu & up-dated with latest security patches.

My wireless connection works fine, BUT when I restart I do not have any connectivity.  All I seem to have to do is go into NETWORK Settings and disable/re-enable the wireless settings (e.g. type the key in again) and it works.  Note that the settings are remembered and visible after reboot (although password is ****'ed out), so it's like their remembered by not picked up correctly.   

[B]QUESTION: Can anyone help me fault find what I need to do so that after a reboot I have wireless connectively in place?
[/B]
Additional background.  I did a ifstat before and after I fixed the connectively after a reboot.  I did note that there was a difference in the wlan0 area in that there is no IPv6 line entry in the first, but there is in the 2nd (working) version.  Not sure if this is significant? 

Not Working (directly after reboot)
```
greg@mythtv:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:D5:59:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:518250 (506.1 KB)  TX bytes:518250 (506.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1C:F0:9D:F6:5B  
          inet addr:10.1.1.236  Bcast:10.1.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-F0-9D-F6-5B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

After resetting wireless (working)
```
greg@mythtv:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:D5:59:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:518525 (506.3 KB)  TX bytes:518525 (506.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1C:F0:9D:F6:5B  
          inet addr:10.1.1.236  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:f0ff:fe9d:f65b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3539 (3.4 KB)  TX bytes:4654 (4.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-F0-9D-F6-5B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

Thanks

---

### Post by Brain-free on 2008-04-29
Which is the chipset of your card? I'm having the same issue with mine. But in gutsy, under the wlan0 section, it clearly stated which was the driver I was using. Now -and I can see this is your case also- it doesn't. Maybe is this some way related to the problem?

---

### Post by callagga on 2008-04-29
If you mean chip set of my wireless card:  I have a D-Link, DWL-G510, 32 bit PCI interface.  I can't see anywhere on the box what chipset it is?

---

### Post by Brain-free on 2008-04-29
I see, it is not the same. I have the buggy rtl8185. When you press restart, after you leave desktop, do you see any warnings, such as "disconnect wlan0"?

---

### Post by callagga on 2008-04-29
not on the display as far as I remember - or did you mean in a log file somewhere?

---

### Post by callagga on 2008-05-13
bump - still having this issue - would love any advice/ideas re how to fix

Should I disable NetworkManager?  per the [wiki link here]("https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5")

---

### Post by callagga on 2008-05-18
(bump) still having problems here

I note that after a reboot that if I run "iwconfig" I see wlan0 doesn't have the router connection in place.  It seems to have dropped it.  That is before the reboot "iwconfig" shows the router connection fine, but not after the reboot.

My /etc/network/interfaces file is as follows.  Does this look OK?

```
greg@mythtv:~/.shepherd$ cat /etc/network/interfaces 
auto wlan0
iface wlan0 inet static
address 10.1.1.236
netmask 255.255.255.0
gateway 10.1.1.1
wpa-psk 3786f0a5ae52822d539dffa4ff0149f164014941326fc1b9f310c106061185a4
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MIXEDUP

auto lo
iface lo inet loopback

```

---

