---
title: "Internet/wireless network stopped working after crash/reboot (Ubuntu 13.10)"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by cederfjard on 2014-04-03
I'm having trouble with my internet connection. It's a wireless network with a D-Link DIR-655 router, the wireless adapter on my computer is a D-Link DWL-G122 (an USB dongle). I'm unable to try with an ethernet cable. I'm on Ubuntu 13.10.

After the system hanged for reasons unclear to me, I rebooted with Alt + SysRq + REISUB. After booting I no longer had internet access. Both Ubuntu and my router says that I'm connected to the network, and that I have the same IP-address. The output of ifconfig is the same as before I think (I can transcribe it if necessary). However, I can't ping any device on the network from the computer, not even the router ("Destination Host Unreachable"). The same is true the other way around too. All other devices on the network are working as usual. I have powercycled both the computer and the router.

I'm pretty lost here, any help would be much appreciated.

Edit: Just to clarify, I can't ping anything on the local network or externally either by hostname or IP-address.
Edit 2: I tried booting from a live USB on the same machine and got internet access, so it's not that the dongle has gone belly-up.

---

### Post by TheFu on 2014-04-03
Excellent troubleshooting. You have just determined that it is a settings or driver issue under ubuntu 
* NOT hardware
* NOT router
* NOT wifi interference.
Extremely helpful.

The output from these commands will be helpful:
[B]
sudo lshw -C network
route
ifconfig[/B]  
and because this is wifi, 
**iwconfig**
Please use "code" tags, so it is readable. My signature explains.

---

### Post by cederfjard on 2014-04-03
TheFu, thank you for your help. It turns out that after booting up once more the issue seems to have disappeared. I'm pretty sure I didn't make any obvious mistakes before, but I'm still pretty embarrassed. :P

Marking this as solved, but I'm still curious what might have been the problem? Knowing of some possible reasons would be helpful if it happens again. I'm appending the output of the commands you listed just in case:

**sudo lshw -C network**
```

  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:55:73:78
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=1.1-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:fdfe0000-fdffffff memory:fdfdb000-fdfdbfff ioport:eca0(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:4
       logical name: wlan0
       serial: 00:22:b0:74:0e:1a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.11.0-18-generic firmware=1.7 ip=192.168.0.16 link=yes multicast=yes wireless=IEEE 802.11bg

```

**route**
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     9      0        0 wlan0

```

**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:1e:c9:55:73:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:fdfe0000-fe000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:610826 (610.8 KB)  TX bytes:610826 (610.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:b0:74:0e:1a  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:b0ff:fe74:e1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16771311 (16.7 MB)  TX bytes:1938410 (1.9 MB)

```

**iwconfig**
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 14:D6:4D:27:9E:12   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:29  Invalid misc:1121   Missed beacon:0

```

---

### Post by TheFu on 2014-04-03
USB is flaky sometimes. Not always a real good connection.

---

