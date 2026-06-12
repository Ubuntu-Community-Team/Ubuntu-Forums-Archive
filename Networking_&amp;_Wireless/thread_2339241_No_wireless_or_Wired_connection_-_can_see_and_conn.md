---
title: "No wireless or Wired connection - can see and connect to router though?!?!"
date: 2016-10-06
forum: Networking &amp; Wireless
---

### Post by rotdog on 2016-10-06
Hi All,

Reasonably new to Ubuntu....

I have version 16.04 and up until a few weeks ago everything was fine but now appear to be suffering chronic connection issues.  I've run dry on my knowledge and looking to see if you might be able to help.  I can both see and connect to my router but am completely unable to connect to the internet.  I have other devices, including further Linux platforms working OK on their connections and have checked that all router settings are not inhibiting the issue.  I can ping these devices all with positive response but am unable to ping outside of this network...having tried both named conventions and IP addresses.

The problem occurred seemingly overnight when I attempted to load up the internet with no changes that I was aware of.

I have included the code and results of a number of commands, hopefully you guys might be able to shed some light on the issues for me.

Cheers

(Apologies for the size of the post)

```


[SIZE=2]-  iwconfig
wlp3s0    IEEE 802.11abgn  ESSID:"TALKTALK-0EACB2"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: E8:CC:18:0E:AC:B2   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:30   Missed beacon:0
lo        no wireless extensions.
enp0s25   no wireless extensions.
-  route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
link-local      *               255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     *               255.255.255.0   U     600    0        0 wlp3s0
-  ifconfig
enp0s25   Link encap:Ethernet  HWaddr f0:de:f1:70:8f:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:183962 (183.9 KB)  TX bytes:183962 (183.9 KB)
wlp3s0    Link encap:Ethernet  HWaddr a0:88:b4:8b:47:3c  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a288:b4ff:fe8b:473c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16664 (16.6 KB)  TX bytes:5845 (5.8 KB)
-  ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=3.17 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=1.36 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=0.974 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=0.889 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=1.27 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=254 time=2.94 ms
^C
--- 192.168.1.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5007ms
rtt min/avg/max/mdev = 0.889/1.769/3.175/0.929 ms
ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7055ms
-  ping -c 5 google.com
ping: unknown host google.com
-  dig google.com
; <<>> DiG 9.10.3-P4-Ubuntu <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 04
       serial: f0:de:f1:70:8f:c6
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:25 memory:f2500000-f251ffff memory:f252b000-f252bfff ioport:5080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 34
       serial: a0:88:b4:8b:47:3c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-31-generic firmware=18.168.6.1 ip=192.168.1.67 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:28 memory:f2400000-f2401fff
[/SIZE]
```

---

### Post by zx6r1033 on 2016-10-06
I was actually coming here to post the same thing. I've surfed through some other posts where people had success fixing this, but none of the fixes worked for me. I think I'll just camp out on your thread and see what turns up. Thanks for beating me to it!

---

### Post by rotdog on 2016-10-06
No problem, if you find out please let me know it's driving me crazy. I've trawled most posts each one being slightly different. And I've exhausted my knowledge and experience levels now.

---

### Post by zx6r1033 on 2016-10-06
Yeah, I am in the same boat. DNS servers, MTU settings, DHCP settings, etc etc etc.  I've been at it for about a week. 

For me, it also is not limited to one PC or one distro. I've tried on 4 different PCs on 3 different networks using Ubuntu, Mint, and Debian. All share this issue.

---

### Post by zx6r1033 on 2016-10-12
I don't have an answer, exactly, but I managed to get my issue resolved. I reset my router back to default settings and started over. Now everything works flawlessly on "Automatic" settings. I guess I had changed something along the way that I shouldn't have. Maybe the same would work for you?

---

### Post by rotdog on 2016-10-16
Hi, I've recently put a new router in and have a new ISP...still no success. I've completely disabled IPv6 and checked named servers within DNS settings. Not that it should make any difference as I don't appear to even have the ability to to ping external addresses even through an IP address.

Ive tried running the troubleshooting script but get no joy there either as it doesn't seem to function correctly even when trying various methods.

i'm down to rescuing as much data as I can a removing Ubuntu to try it all again. As I said other computers running Ubuntu (albeit older versions) seem to work just fine on the same router. But I have some newer devices (android boxes) running Linux environments that appear to suffer with connection issues as well.

Im stumped....

---

### Post by jeremy31 on 2016-10-16
Please try what is posted [https://ubuntuforums.org/showthread.php?t=2339517&p=13557267#post13557267](https://ubuntuforums.org/showthread.php?t=2339517&p=13557267#post13557267) in just the one post by chili555 and see if power management is causing the issue

---

### Post by rotdog on 2016-10-16
Hi, just went to open and brings up a blank document...nothing it it

---

### Post by jeremy31 on 2016-10-16
You must still have the older version of network-manager.  Is UFW enabled?

---

### Post by rotdog on 2016-10-16
Yes, but I've tried to disable it and still got nothing.

Happy to try anything though under guidance.

---

### Post by rotdog on 2016-10-16
Just double checked and got nothing.

---

### Post by rotdog on 2016-10-16
Just tried agin and nothing

---

### Post by jeremy31 on 2016-10-16
Did you use Network Manager to set a static IP on the computer?  Have you restarted the router?  Since it is an Intel wireless, try
```
sudo modprobe -r iwlwifi
```
```
sudo modprobe iwlwifi 11n_disable=8
``` 
That will enable aggressive TX and could possible help.  The aggressive TX will be enabled until you reboot

What happens that you can't get the wireless script to work?

---

### Post by rotdog on 2016-10-16
Tried a static address and copied over subnet mask and router (gateway) settings from another device.  None of which were successful.  This was all done post router reboot and computer reboot with the firewall disabled.

Also just tried the mod probe comman with no success, also tried repeating the steps with this command complete, just as above.

Not sure why the script does vnot run as it it comes up with the text file, run is activated but then nothing at all happens from there on in.

---

### Post by jeremy31 on 2016-10-16
Can you access the router page in Firefox using 192.168.1.1
If UFW is off ```
dmesg | grep -i ufw
```
should have no results.  I would see if there are logs on the router that may reveal why you can't ping 8.8.8.8

---

