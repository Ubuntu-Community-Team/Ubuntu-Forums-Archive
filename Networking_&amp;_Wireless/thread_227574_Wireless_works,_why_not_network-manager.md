---
title: "Wireless works, why not network-manager"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by unconquerable on 2006-08-01
**FIXED THIRD POST DOWN**

My wireless works great at the moment.  My only complaint is fast switching of wireless networks.  I downloaded network-manager-gnome for this reason.  After a restart the icon shows an exclamation point.  Even though I am connected to the internet wirelessly, It shows no interent connection when hovered over.  When clicked it has only one option of 'wired network' but it is greyed out.

my wirless card is being recognized as eth1 instead of wlan0 is that the problem.

Look at my printouts they think that it is ethernet even though it connects ok wirelessly.  How can I get this to work correctly.

**iwconfig**

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Miller"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B3:32:3B:93
          Bit Rate:48 Mb/s   Tx-Power:14 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/100  Signal level=-73 dBm  Noise level=-74 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1975   Missed beacon:0

sit0      no wireless extensions.


**ifconfig**

> eth0      Link encap:Ethernet  HWaddr 00:16:D3:04:A3:FE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:13:02:5C:68:25
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe5c:6825/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15729 errors:0 dropped:1975 overruns:0 frame:0
          TX packets:5925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10059606 (9.5 MiB)  TX bytes:597805 (583.7 KiB)
          Interrupt:185 Base address:0xe000 Memory:d4000000-d4000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)


---

### Post by amp_man on 2006-08-02
did you follow the [wiki](https://help.ubuntu.com/community/WifiDocs/NetworkManager)? that article got it up and running for me in 5 minutes tops.

---

### Post by unconquerable on 2006-08-02
The wiki did not help.  THIS FIXED MY network-manager problems

I changed the interface name from eth1 to wlan0,  it seems that since it saw it has a ethernet connection, I was not allowed to quick swap networks.

Now it works!

> 
edit /etc/iftab

change:

eth1 mac your-wireless-card-mac-address

to

wlan0 mac your-wireless-card-mac-address

---

### Post by codepoetmc on 2006-08-02
Thank You! That was the last piece to the puzzle. I followed [this post]("http://www.ubuntuforums.org/showthread.php?t=201902") to get ndiswrapper working, but I think this little part was missing (at least for me). It may be in the replies, but there were entirely to many for my ADHD afflicted self to read.

---

### Post by detyabozhye on 2006-08-17
Awesome man, works great!

---

### Post by detyabozhye on 2006-08-18
Um, after I tried this, I can't access the laptop from my desktop via ssh, samba, or vnc anymore, does anybody know what the problem could be?

---

### Post by brazzy on 2006-08-19
Well, my wi-fi PCI card is seen as "eth2" and not "wlan0"... Could this be the reason why even if it's right configured with ndiswrapper I cannot connect to my router?
How can I change its name?

---

### Post by iseebluuue on 2006-09-09
> **unconquerable said:**
> The wiki did not help.  THIS FIXED MY network-manager problems

I changed the interface name from eth1 to wlan0,  it seems that since it saw it has a ethernet connection, I was not allowed to quick swap networks.

Now it works!


good thinking man! i changed the interface, restarted, and now it's as good as gold!

---

