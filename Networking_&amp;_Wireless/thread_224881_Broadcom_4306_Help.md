---
title: "Broadcom 4306 Help"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by mkw87 on 2006-07-28
Alright, so I have converted most of my desktop usage to ubuntu, and I'm trying to convert my g/f's laptop, though she's hesitant, and guess what card her wireless is?  Apparently the rev 2 Broadcom 4306 cards do not play well with ubuntu, so I set off following [this](http://ubuntuforums.org/showthread.php?t=201902&referrerid=126820) howto, because it did not use the firmware cutter (I figured the less hacking, the less that would go wrong in the future, she has a small amount of patience :P).  

I had no troubles getting through it at all, but when I finished, next to the network computers in the information area, is a small red diamond which I assume means not good because it isnt there if I plug in a land line to the lappy (which works fine at least).  The driver and hardware are both recognized, just no network transfers go through.  I have my linksys WRT54G with dd-wrt set to broadcast ssid, the wireless is in mixed mode for now, and no wep or wpa is set up.

This is all a brand new install of dapper, fully updated after I installed from the live cd.  Any help to troubleshoot this is MUCH appreciated (as I have ready many HowTo's but I'm still too new to linux to know exactly what is going on, and I prefer to not just blindly type stuff in until it 'magically' works, I prefer to understand whats going on).

---

### Post by mkw87 on 2006-07-28
The following is the output of various commands to help with troubleshooting:

iwconfig:
```
jennifer@winn:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```


lspci | grep Broadcom\ Corporation
```
jennifer@winn:~$ lspci | grep Broadcom\ Corporation
0000:00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```


ifconfig
```
jennifer@winn:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:C9:C8:02
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fec9:c802/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:921 errors:0 dropped:0 overruns:0 frame:0
          TX packets:885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:673118 (657.3 KiB)  TX bytes:132627 (129.5 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:45:10:11
          inet6 addr: fe80::290:4bff:fe45:1011/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d0004000-d0006000
```

Again, thanks for the help.

---

### Post by mkw87 on 2006-07-29
I found a tip somewhere to change eth0 to wlan0 in 3 places, one being /etc/iftab, but that file is emtpy/does not currently exist.  Not sure if there was a problem with install the driver or not, maybe I'll reinstall it.

---

### Post by mkw87 on 2006-07-29
Ok, I installed gnome network manager and got the wireless to show up there, but when I try to connect, I enter my WEP key, and it tries to connect but never succeeds.  The router sees the computer, but the computer was broadcasting at 2.462GHz and not the default 2.437GHz, so I changed the router, but that didn't seem to fix things.

Anyone have any idea?

---

