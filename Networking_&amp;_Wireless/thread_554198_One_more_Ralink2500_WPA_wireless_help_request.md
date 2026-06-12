---
title: "One more Ralink2500 WPA wireless help request"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by The-Twitching-Peanut on 2007-09-18
Hi all,

I just installed Ubuntu Feisty Fawn 7.04 x64 on my laptop,  and as you may have guessed from the thread title I can't connect to my router using a Static IP and WPA-PSK encryption, now I have followed a few on-line tutorials but, out of frustration, I have decided to swallow my pride and ask for help....god I hate feeling like a n00b.

Below are some details about my x64 setup:
[LIST=1]
[*]Dual boots with XP Pro
[*]Ralink2500 wireless adapter (built in internal)
[/LIST]

Router is a Netgear DG834GT and is set up as:
[LIST=1]
[*]MAC filtering and assignment of static IP to all attached devices
[*]WPA-PSK encryption
[*]SSID broadcast turned off
[/LIST]

I know that my card can connect to my router as it does so under XP and it does support WPA and to save me the hassle of switching between XP and Linux I have connected the laptop to the router with an Ethernet cable and can get on the net with no probs.

Firstly:

ndiswrapper and ndisgtk is installed as is wifi radar.

Now when I execute:

```
ifconfig
```

I receive this output:

```

eth0      Link encap:Ethernet  HWaddr 00:03:0D:33:6A:A7  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe33:6aa7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1068227 (1.0 MiB)  TX bytes:220834 (215.6 KiB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3480 (3.3 KiB)  TX bytes:3480 (3.3 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:17:64:A4  
          inet addr:192.168.168.3  Bcast:192.168.168.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe17:64a4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:857568 (837.4 KiB)
          Interrupt:19 Base address:0xc000 

```

I have manually edited my interfaces file located under /etc/interfaces with the following:

```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.168.3
gateway 192.168.168.1
dns-nameservers 192.168.168.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid Twitchville
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk omitted for security

```

When I execute:

```
iwconfig
```

I receive:

```
ra0       RT2500 Wireless  ESSID:"Twitchville"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=24 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-31 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I would really appreciate it if someone could guide me through this as I am quite frustrated by this and feel as though I am going round in circles, but thanks for at least reading this.

Twitch

---

### Post by kevdog on 2007-09-19
Use the instructions here as a guide and modify according to your situation:

If you are using WPA security on your wireless network, then your /etc/network/interfaces file should look like this:

Code:

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra

Thanks to peterthewolf, sefs & Austin_KW for helping with this part.

If you are using a static IP address (i.e. the DHCP server on your router doesn't assign you one), use these settings (thanks to kevdog)

Quote:
Just to follow-up, one of the users I was helping posted this about getting a static IP address to work. I thought I would pass it along for the sake of completeness

Code:

auto wlan0
iface wlan0 inet static
address STATIC_IP_ADDRESS
netmask 255.255.255.0
network ROUTER_IP
gateway ROUTER_IP
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid YOUR_ESSID
        pre-up iwconfig wlan0 mode Managed

Of course, you'll need to add settings for WEP and WPA, depending on which one you're using.

---

### Post by The-Twitching-Peanut on 2007-09-19
Thanks for your response,

I have edited my interfaces code with using your example as a template and this is what I have:

```
auto ra0
iface ra0 inet static
address 192.168.168.9
netmask 255.255.255.0
network 192.168.0.1
gateway 192.168.0.1
pre-up ifconfig ra0 up
pre-up iwconfig ra0 essid Twitchville
pre-up iwconfig ra0 mode Managed
dns-nameservers 192.168.168.1
wpa-driver wext
wpa-ssid Twitchville
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk omitted

```

I did also notice that the Mac address for my wireless was not listed under my router settings, so I added it and assigned it its own IP.

Is the above code correct, as I cannot still connect?

Twitch

---

### Post by kevdog on 2007-09-19
Im not sure if you need the dns-nameservers line, Just comment it out.

Look at the example I posted above.  Remove all the wpa lines from your post.  These are not correct and will not work with ra based cards.

These are the WPA statements:

pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
pre-up iwpriv wlan0 set SSID="YOUR_SSID"
pre-up iwpriv wlan0 set NetworkType=Infra

---

### Post by The-Twitching-Peanut on 2007-09-19
Thanks Kevdog,

I've amended my file as described but alas no luck.

I did notice when I executed a particular command from the terminal (I forget what it is) I received the output that the installed ralink driver was invalid.

I removed it and installed a different one I had and it appeared to work some what.

I have switched over to WICD and removed all the other network management progs I had installed and have some progress.

Using WICD my card can see the network (although it shows it as secured WEP, even though its WPA-PSK) and upon entering all the relevant details (IP, subnet etc) it appears to connect but I have no internet.

Also when pinging the router using the wireless card I get a host unreachable response.

Any thoughts?

Kind regards

Twitch

---

### Post by kevdog on 2007-09-19
Can you post 

lshw -C network

Did you install the wpasupplicant package?

---

### Post by The-Twitching-Peanut on 2007-09-19
Hi,

wpasupplicant is installed and the output of lshw -c network

```

jason@jason-laptop:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:33:6a:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.5 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:febfc000-febfcfff irq:19
  *-network:1 DISABLED
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 01
       serial: 00:11:09:17:64:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 link=no multicast=yes wireless=RT2500 Wireless
       resources: iomemory:febf8000-febf9fff irq:19

```

HTH

---

### Post by kevdog on 2007-09-19
Thats strange -- I see the rt2500STA driver assigned but it states disabled.

I know you are using the wired connection now, but does it state disabled even when trying to use the wireless connection without the wired connection??


Another idea -- update the rt2500 driver.  Take a look at this thread its for the rt73 drivers.  The process for updating your driver is exactly the same except you want rt2500 rather than rt73.  So just type 2500 in the thread everywhere 73 is mentioned.

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by The-Twitching-Peanut on 2007-09-19
When I connect the wireless w/o the wired this is the output:

```

jason@jason-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:33:6a:a7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 multicast=yes
       resources: ioport:d800-d8ff iomemory:febfc000-febfcfff irq:19
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 01
       serial: 00:11:09:17:64:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 ip=192.168.0.3 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:febf8000-febf9fff irq:19


```

I have updated my driver according to the instructions given in the link and it still does not work.

For reference here is a copy of my current interfaces file:

```

auto ra0
iface ra0 inet static
address 192.168.0.3
netmask 255.255.255.0
network 192.168.0.1
gateway 192.168.0.1
pre-up ifconfig ra0 up
pre-up iwconfig ra0 essid Twitchville
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="removed"
pre-up iwpriv ra0 set SSID="Twitchville"
pre-up iwpriv ra0 set NetworkType=Infra

```

---

### Post by kevdog on 2007-09-19
Can you post a few things:

modinfo rt2500

Just want to check something.

Can you adjust the router settings and see if you can connect without encryption??? Just want to confirm the driver works.

Does iwlist ra0 scan present any output??

I dont think these lines are needed:
pre-up iwconfig ra0 essid Twitchville
pre-up iwconfig ra0 mode Managed

Have you just tried connecting from the command line only:

Something like this (but ra0 instead of wlan0)
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwpriv wlan0 set AuthMode=WPAPSK
sudo iwpriv wlan0 set EncrypType=TKIP
sudo iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
sudo iwpriv wlan0 set SSID="YOUR_SSID"
sudo iwpriv wlan0 set NetworkType=Infra
sudo dhclient wlan0

Can you post output of iwpriv??

---

### Post by trooper666 on 2007-09-19
try this:
------------------
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.100

auto ra0
iface ra0 inet static
	address 192.168.1.5
	netmask 255.255.255.0
	gateway 192.168.1.100
	pre-up ifconfig ra0 up
	pre-up ifconfig ra0 down
	pre-up ifconfig ra0 up
	pre-up ifconfig ra0 down
	pre-up iwconfig ra0 essid "your network name"
	pre-up iwconfig ra0 mode Managed
	pre-up iwpriv ra0 set AuthMode=WPAPSK
	pre-up iwpriv ra0 set EncrypType=AES
	pre-up iwpriv ra0 set WPAPSK="your wpa key"
	pre-up ifconfig ra0 up

-------------

this works for me, restart the comp to avoid any compl.

---

### Post by odiseo77 on 2007-09-19
Hi, I have the same wireless card and similar settings (only the IP address is not static, but assigned via DHCP) and everything is working perfectly here. If this helps, this is the guide I followed in order to make it work: [http://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](http://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500) (click on item 3.2, "WPA Info").

---

### Post by The-Twitching-Peanut on 2007-09-20
> **kevdog said:**
> Can you post a few things:

modinfo rt2500

Just want to check something.

Can you adjust the router settings and see if you can connect without encryption??? Just want to confirm the driver works.

Does iwlist ra0 scan present any output??

I dont think these lines are needed:
pre-up iwconfig ra0 essid Twitchville
pre-up iwconfig ra0 mode Managed

Have you just tried connecting from the command line only:

Something like this (but ra0 instead of wlan0)
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwpriv wlan0 set AuthMode=WPAPSK
sudo iwpriv wlan0 set EncrypType=TKIP
sudo iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
sudo iwpriv wlan0 set SSID="YOUR_SSID"
sudo iwpriv wlan0 set NetworkType=Infra
sudo dhclient wlan0

Can you post output of iwpriv??

The output of 

```

modinfo rt2500:

filename:       /lib/modules/2.6.20-16-generic/extra/rt2500.ko
license:        GPL
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 CVS 2007091914
author:         http://rt2x00.serialmonkey.com
srcversion:     57C1967353B0E2C296C6145
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           ifname:Network device name (default ra%d) (charp)


```

I can connect to the router w/o WPA enabled.

When I execute iwlist ra0 scan, I receive this output (tried with both encryption on and off)

```
ra0       Interface doesn't support scanning.

```

After invoking sudo dhclient ra0 without connecting with WICD:

```

There is already a pid file /var/run/dhclient.pid with pid 11488
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:11:09:17:64:a4
Sending on   LPF/ra0/00:11:09:17:64:a4
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 128645 seconds.

```

After invoking iwpriv:

```

lo        no private ioctls.

eth0      no private ioctls.

ra0       Available private ioctls :
          set              (8BE2) : set 1024 char  & get   0      
          bbp              (8BE3) : set 1024 char  & get 1024 char 
          mac              (8BE5) : set 1024 char  & get 1024 char 
          e2p              (8BE7) : set 1024 char  & get 1024 char 
          rfmontx          (8BEC) : set   2 int   & get   0      
          get_rfmontx      (8BED) : set   0       & get   1 int  

```

---

### Post by kevdog on 2007-09-20
Can you post lshw -C network

---

### Post by The-Twitching-Peanut on 2007-09-20
With encryption enabled:

```

  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:33:6a:a7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: ioport:d800-d8ff iomemory:febfc000-febfcfff irq:19
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 01
       serial: 00:11:09:17:64:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:febf8000-febf9fff irq:19

```

Without and connected via WICD:

```

  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:33:6a:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:febfc000-febfcfff irq:19
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 01
       serial: 00:11:09:17:64:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 ip=192.168.0.5 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:febf8000-febf9fff irq:19


```

Without encryption and not connected via WICD:

```

  *-network:0 DISABLED    
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:33:6a:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:febfc000-febfcfff irq:19
  *-network:1 DISABLED
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@00:0b.0
       logical name: ra0
       version: 01
       serial: 00:11:09:17:64:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:febf8000-febf9fff irq:19

```

---

