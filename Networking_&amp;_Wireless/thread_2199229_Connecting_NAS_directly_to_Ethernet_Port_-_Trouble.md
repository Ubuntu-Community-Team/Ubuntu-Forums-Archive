---
title: "Connecting NAS directly to Ethernet Port - Troubleshoot"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by a_c_dwyer on 2014-01-12
Hello ubuntu community,

I have a DLINK DNS-320L and I was able to successfully connect it when connecting it to my wireless router. Since moving to a new apartment however, I do not have access to the router and I'm attempting to connect it via a crossover cable directly to my computer. I've ran out of ideas to try (at the moment, my level of expertise with networking is trial and error). Could you please help run me through some troubleshooting to get this thing connected!?

Much appreciated
Adam

**DLINK support told me this:**
"You need to setup static IP on your ubuntu system for e.g. 192.168.0.99, subnet mask as 255.255.255.0 and default gateway as 192.168.0.32 and then you can login with 192.168.0.32"

**Things I tried:**

**1 - Using the instructions here to set static IP (by editing "/etc/network/interfaces"):**

Official Documentation - Network Configuration - Static IP Address Assignment - [https://help.ubuntu.com/10.04/serverguide/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/network-configuration.html)
Result - ethernet connection disappears from system tray list
[B]
2 - Edited connection through system tray[/B]

Set IPv4 method to Manual with address, netmask and gateway as per DLINK support instructions.
Result - Connection status gets stuck on "Preparing to connect"

**3 - Recommendations provided here (IPv4 method: link local):**

Connecting NAS directly to Ethernet Port - [http://ubuntuforums.org/showthread.php?t=2004541](http://ubuntuforums.org/showthread.php?t=2004541)
Result - Connection status gets stuck on "Preparing to connect"

---

### Post by Iowan on 2014-01-12
All three methods *should* work. 
1. Manually configuring the interface _will_ make it disappear from the system tray - since Network Manager no longer has control.

2. Are you still set to "Connect Automatically"?

3. Haven't used this one... 


Have you checked **ifconfig** to see if the machine gets an IP address?

---

### Post by a_c_dwyer on 2014-01-12
Thanks Iowan

**Re: Automatically connect to this network**
I wasn't set to automatically connect, so I just tried that and... progress (it seems)! After a reboot (and only after a reboot), the connection status went to "connected"

Continuing with method** 2. **above, and running **ifconfig** I get:

```
eth0      Link encap:Ethernet  HWaddr 00:26:b9:02:7f:eb  
          inet addr:192.168.0.99  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe02:7feb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12484 (12.4 KB)  TX bytes:16866 (16.8 KB)
          Interrupt:17 
```

... followed by printout for "lo" and "wlan0"

I tried looking under network in dolphin, then tried the potential IP addresses in a web browser but nothing is found. Could you please let me know where to go from here to actually access the files on the drives?

---

### Post by steeldriver on 2014-01-12
Is 192.168.0.32 a default IP for the NAS? or a static IP you previously configure it to when it was connected via the router?

You might want to try installing nmap and then running a ping scan to verify the IP

```
nmap -sP 192.168.0.0/24
```

---

### Post by Iowan on 2014-01-12
This is where my background with NAS boxes runs out...
You can **ping 192.168.0.32 -c3** to verify the connection.
If the connection exists, you might try **smbtree** to see if shares appear.

(Slow typing again...)

---

### Post by a_c_dwyer on 2014-12-28
Hello everyone, I resolved this and am now accessing my NAS drive directly from my laptop via crossover cable. Here are three things I did that made it work:

1 - accessed NAS via router to change LAN mode from DCHP to Static IP
2 - made workgroup the same
3 - made eth0 IPv4 address different than the NAS IP

---

