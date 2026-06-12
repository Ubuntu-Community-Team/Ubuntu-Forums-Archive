---
title: "Can't connect to university DHCP network, no problem with home network"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by tfglynn on 2014-01-05
I'm running 64-bit Ubuntu 13.10 on an Inspiron 15z laptop. Since installing Ubuntu, I have had no problem connecting to my home network. When I was running Windows 8, I had no problem connecting to my university's DHCP network. Now, however, I can't connect to their network either by wifi or ethernet. When I try to connect, I am asked for a username and password, as usual. When I enter my information, I wait, and then I am asked again. I have tried connecting while running an Ubuntu 13.10 live CD, with no success.
Here is the output when I enter "ifconfig" in the terminal:
```

eth0      Link encap:Ethernet  HWaddr 78:45:c4:c1:f6:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9660 (9.6 KB)  TX bytes:9660 (9.6 KB)
 
wlan0     Link encap:Ethernet  HWaddr 60:36:dd:dc:d4:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1440 (1.4 KB)  TX bytes:716 (716.0 B)

```

And here is (I think?) the relevant info from "lspci":
```

07:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
            Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN
            Flags: bus master, fast devsel, latency 0, IRQ 46
            Memory at f7900000 (64-bit, non-prefetchable) [size=8K]
            Capabilities: <access denied>
            Kernel driver in use: iwlwifi
 
09:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
            Subsystem: Dell Device 057e
            Flags: bus master, fast devsel, latency 0, IRQ 49
            Memory at f7800000 (64-bit, non-prefetchable) [size=256K]
            I/O ports at d000 [size=128]
            Capabilities: <access denied>
            Kernel driver in use: alx

```

Any help in solving this issue would be greatly appreciated.

Update: I've successfully connected to an ethernet port in my dorm. It's orange, and most of the ports are white. This is the part where I confess that I don't know what I'm doing. The wifi still doesn't work, though, and most of the ethernet ports seem not to work; I see "not connected" in my wired network menu when trying to connect via them. Based on what I've heard from classmates, though, those other ports might be defective.
Also, I've been able to connect to a neighbor's private wifi.

**Update2:** I've solved the problem on my own. My authentication was set to "Tunneled TLS." Changing it to "PEAP" allowed me to connect.

---

