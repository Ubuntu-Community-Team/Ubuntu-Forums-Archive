---
title: "Yet another wireless problem"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by Master_Legacy on 2011-08-21
Running 11.04 and installed an update earlier today.  After the reboot I haven't been able to connect to wireless.  The wireless card is detected just fine, and I can even see the list of wireless networks available.  but trying to connect to it just times out.

I'm seeing this in syslog:

```
ubuntu NetworkManager[960] <warn> (wlan0): DHCPv4 requested timed out.
ubuntu NetworkManager[960] <info> (wlan0): cancelled DHCP transaction, DHCP client pid 1958
...
bunch of other "timed out" messages
...
ubuntu NetworkManager[960] <warn> Activation (wlan0):  Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)

```

From the terminal I also tried running:
```

$ lspci | grep work
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


```
I tried restart the computer into the previous kernel that was installed before the update, same problems.  Not sure what else to try

Anyone have any clues?  Keeping in mind, plugging this machine through a wired connection isn't really an option at the moment, so downloading anything to install/reinstall will have to happen on another machine then copied over USB...

---

### Post by fdrake on 2011-08-21
can you post your :
```
iwconfig
or
ifconfig
```

---

### Post by Master_Legacy on 2011-08-21
```
$ iwconfig
lo       no wireless extensions.

eth0     no wireless extensions.

wlan0    IEEE 802.11abgn ESSID:off/any
         Mode: Managed Frequency:2.412 GHz Access Point: Not-Associated
         Tx-Power=18 dBm
         Retry  long limt:7   RTS thr:off    Fragment thr:off
         Power Management:off

```

```
$ ifconfig
eth0    Link encap:Ethernet HWaddr b8:ac:6f:a25b:ed
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         Rx packets: 0 errors:0 dropped:0 overruns:0 frame:0
         Tx packets: 0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 KB)  TX bytes:0 (0.0 KB)
         Interrupt:18

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         Rx packets: 104 errors:0 dropped:0 overruns:0 frame:0
         Tx packets: 104 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:7440 (7.4 KB)  TX bytes:7440 (7.4 KB)

wlan0    Link encap:Ethernet HWaddr 78:e4:00:bf:63:f4
         inet6 addr: fe80::7ae4:ff:febf:63f4/64 Scope:Link
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         Rx packets: 16 errors:0 dropped:0 overruns:0 frame:0
         Tx packets: 24 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:3259 (3.2 KB)  TX bytes:6327 (6.3 KB)

```

EDIT:  So for some bizarre reason resetting the router fixed this problem, even though we had 5 other devices that were able to connect to our wifi that whole time.

-_-

---

### Post by fdrake on 2011-08-21
> 
EDIT:  So for some bizarre reason resetting the router fixed this problem, even though we had 5 other devices that were able to connect to our wifi that whole time.

-_-

funny that you said that. in other posts some ppl did the same and it did not work. I am too cynic sometimes..:)

---

