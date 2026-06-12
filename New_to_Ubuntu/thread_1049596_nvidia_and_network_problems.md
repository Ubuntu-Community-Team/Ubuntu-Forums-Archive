---
title: "nvidia and network problems"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by minsf on 2009-01-24
> **Mellifluous said:**
> I'm having exactly the same problem as the OP! I'm a complete newb to Linux. I just installed Ubuntu 8.10 on my laptop. Unfortunately my wireless card won't connect for some reason and I have this problem with the nvidia drivers. Here is the output of the jockey thing:

xorg:nvidia-173 - NVIDIA accelerated graphics driver (version 173) (Proprietary, Disabled, Not in use)
kmod:wl - wl (Proprietary, Enabled, In use)
xorg:nvidia-177 - NVIDIA accelerated graphics driver (version 177) (Proprietary, Disabled, Not in use)

The driver downloads but then nothing happens. Help!
MELLIFLUOUS, i'm starting this new thread for you, because you posted this inside a bit irrelevant thread. This way people can help you without reading 6 pages before they get to your post :)

to the point- we need more information so that we can help better:
are you using a laptop/desktop? vendor? model?
what kind of monitor do you use?

* for the following, you will need to know how to get to a command line interface (CLI): if you have gnome, you can open terminal Applications>Accessories>Terminal. if you have kde (kubuntu), open Konsole. if you get a black screen after boot (i mean, after the ubuntu splash screen with the orange bar), try ALT+CTRL+F1 (you may be asked for your password).

to give us more info, in a command line interface type the following command and hit enter. you may be asked for your password. post here the output:
```
sudo dpkg -l | grep nvidia
``` 
(to see what nvidia drivers are currently installed)
```
sudo lshw -C display
```
(to get some info about your graphic card)

---

### Post by minsf on 2009-01-24
regarding the network problem: post here the output of
```
sudo lshw -C network
``` 
(info about your network cards)
```
ifconfig -a |less
```
info about your network configuration
```
iwconfig
```
info about your wireless network

---

### Post by RichardLinx on 2009-01-24
Did you restart your computer after installing the driver? I had the same issue once and even after a reinstall the graphics card didn't work. After that I just reinstalled It and It worked fine. I suggest you try that if you already haven't.

---

### Post by Mellifluous on 2009-01-25
Thanks for your help! I'm using a Dell Inspiron 1520 laptop with XP dual-boot.

Output of sudo lshw -C display is:

```
SCSI                      
  *-display UNCLAIMED
       description: VGA compatible controller
       product: GeForce 8400M GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
```

Output of sudo dpkg -l | grep nvidia is:

```
ii  nvidia-173-modaliases                     173.14.12-1-0ubuntu4                  Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-177-modaliases                     177.80-0ubuntu2                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                      71.86.04-0ubuntu10                    Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                      96.43.05-0ubuntu10                    Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                             0.2.4                                 Find obsolete NVIDIA drivers
```

Output of network codes as follows, in order:

```
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a0:71:db
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.66 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:d9:0c:41:3b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 52:71:86:ec:58:bc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:a0:71:db  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fea0:71db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3027 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3825157 (3.8 MB)  TX bytes:212373 (212.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

pan0      Link encap:Ethernet  HWaddr 52:71:86:ec:58:bc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:0c:41:3b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-D9-0C-41-3B-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

Phew, that's a lot of info :confused:

---

### Post by Mellifluous on 2009-01-25
Any ideas anyone? As a new Linux user I'm a bit overwhelmed at all the technical stuff I have to do to get basic things working :(

---

### Post by minsf on 2009-01-26
in a command line interface run (while connected to the internet)
[CODE]sudo apt-get install nvidia-glx-180[CODE]
and reboot

* please post here any error (starting with "E:")
* if after reboot and after the ubuntu splash screen, you get a blank screen, you can get to the command line via ctrl+alt+f1. you will then need to edit your /etc/X11/xorg.conf file. i will be glad to help you with the editing. in this stiuation, if you dont have another computer, you can get to the internet by booting from the live CD.

---

