---
title: "Wi-fi connected, but ping to router times out"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by stanislav-schmidt on 2014-06-17
I have no problems with the wi-fi connection at the uni or anywhere else, but as soon as I connect to my new router at home, the network manager shows that I'm connected, but all connections time out, even to the router itself. Also, when I boot to windows on the same laptop or use my mobile phone the connection works fine. So it's only the combination ubuntu+router that doesn't work. Have you an idea how I can troubleshoot it?

---

### Post by Bucky Ball on 2014-06-17
If you click on the network icon and 'Edit Connections' then go to Wireless and the connection with the name of your network, what does it say under the IPv4 settings? You may need to manually set a connection to your access point to automatically connect when it's in range. Add the home network's name at the very least and any other details you have. You're not using a static IP but receiving your IP address via DHCP from your router? 

Please supply the output of these commands, one at a time and in ```
 tags. Thanks. ;)

[code]sudo lshw -C network
iwconfig
ifconfig

```
That might give some clues ...

---

### Post by stanislav-schmidt on 2014-06-17
Thanks for helping!

I get the following output:
```

stan@stan-ThinkPad-T530:~$ sudo lshw -C network
[sudo] password for stan: 
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 3c:97:0e:bc:51:6f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f3a00000-f3a1ffff memory:f3a3b000-f3a3bfff ioport:6080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a4:4e:31:38:86:84
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=18.168.6.1 ip=192.168.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:f3000000-f3001fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: a2:2a:74:9f:72:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_mbim driverversion=22-Aug-2005 firmware=CDC MBIM link=no multicast=yes

```

```
stan@stan-ThinkPad-T530:~$ iwconfig
wwan0     no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"o2-WLAN86"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 9C:80:DF:4C:A1:70   
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
stan@stan-ThinkPad-T530:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 3c:97:0e:bc:51:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f3a00000-f3a20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:34743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9998018 (9.9 MB)  TX bytes:9998018 (9.9 MB)

wlan0     Link encap:Ethernet  HWaddr a4:4e:31:38:86:84  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a64e:31ff:fe38:8684/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:836592 errors:0 dropped:1 overruns:0 frame:0
          TX packets:173932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:326408831 (326.4 MB)  TX bytes:41977315 (41.9 MB)
```

```
stan@stan-ThinkPad-T530:~$ ping -c 10 -v 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9071ms
```

Note that the last output shows that although I'm connected to the router, the ping for the router times out, which I find really strange.

Also, what I have observed is that if I log into windows on the same notebook, and restart the router through the browser interface, and log back into ubuntu, then the internet connection works again. I have really no idea how to explain this.

---

### Post by stanislav-schmidt on 2014-06-22
Just to provide some more information about the problem: this is how I usually experience it:
1) I'm at home and my connection works.
2) I put ubuntu to suspend mode and go to my office where I use another wi-fi connection. Suspending the laptop at work and turning it on again doesn't affect the connectivity
3) I go back home with my ubuntu again in suspend mode
4) After resuming ubuntu at home the wi-fi connects, but all connections time out, as described above (even the connection to the router itself). Rebooting the PC does not help.
5) I boot to windows (I  have dual boot), the connection works there and I reboot the router through the web interface (i don't have physical access to the router).
6) I reboot back to ubuntu, the wifi works now.

---

