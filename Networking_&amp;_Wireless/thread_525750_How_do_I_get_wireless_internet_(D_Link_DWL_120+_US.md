---
title: "How do I get wireless internet? (D Link DWL 120+ USB Adapter)"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by taikuodo on 2007-08-14
Im using Ubuntu 7.04 and I tried Ndiswrapper + ndisgtk and the XP drivers that came with the usb adapter (Dlink)

This doesnt seem to work, it says hardware detected but when I say configure networks, theres no wireless option.

---

### Post by taikuodo on 2007-08-14
by the way, now I tried WICD 1.3.1 and it doesn't even detect my wireless usb adaptor...

---

### Post by arijarot on 2007-08-14
Have you tried to config it using NetworkManager?

---

### Post by taikuodo on 2007-08-14
yes, i have tried both. both do not even show a "wireless" option. Its like my adapter doesn't even exist.

---

### Post by imdano on 2007-08-14
Whats the output of these commands (make sure the card is plugged in) ```
sudo lshw -C network
lsusb
iwconfig
ifconfig
```

---

### Post by taikuodo on 2007-08-15
Yeah, Im a complete newb to linux, but not computers. Yes the card is plugged in, and do you mean i should input that code into terminal or something?

Thanks for the help.

---

### Post by yogo on 2007-08-15
Yes do those commands and the output will either show your card or not show it and will tell of your drivers.

On mine. to start mine I have to (Sometimes) use sudo dhclient ra1

---

### Post by imdano on 2007-08-15
Yeah input each of those into the terminal.  All of them will spit back some output, which I want to you to paste here.

---

### Post by yogo on 2007-08-15
all of em

---

### Post by thefoolisme on 2007-08-15
Yes all four separate commands - enter them one by one into the terminal, then copy and paste the results here

---

### Post by taikuodo on 2007-08-16
*-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 22
       serial: 00:1a:4d:40:56:e2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:f8000000-f8003fff ioport:b000-b0ff irq:16
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       serial: 00:40:05:57:2f:c1
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 003 Device 002: ID 2001:3b00 D-Link Corp. [hex] 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions


eth0      Link encap:Ethernet  HWaddr 00:1A:4D:40:56:E2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:4D:40:56:E2  
          inet addr:169.254.7.55  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3764 (3.6 KiB)  TX bytes:3764 (3.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:40:05:57:2F:C1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:40:05:57:2F:C1  
          inet addr:169.254.5.209  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1



Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ral: ERROR while getting interface flags: No such device
ral: ERROR while getting interface flags: No such device
Bind socket to interface: No such device



This is all of them, I just copy and pasted them into one big text file so.

---

### Post by thefoolisme on 2007-08-16
I had a similar problem with a DWL-122 USB adapter.  I think it's about the same vintage as yours, which was why I was following this thread.  

From your post, it looks as though it is reading your USB Ethernet adapter.  That means you might be a step ahead.  Mine didn't show up at all in any of the config runs I did in Terminal.  I got mine working last night after installing "linux-wlan-ng", which includes the drivers for my USB LAN.  I did not need to use NDISWrapper.  

I used bits of information from these posts to get it up and running:
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)
[http://ubuntuforums.org/archive/index.php/t-4041.html](http://ubuntuforums.org/archive/index.php/t-4041.html)
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Since it seems to be reading your WLAN0, have you tried restarting your PC with the network cord unplugged?  I couldn't get mine to configure correctly until after I had unplugged it, because it kept trying to restart the ethernet connection.  Also, do you have the Network ID available?  And is your wireless connection encrypted?  If so, you'll need to know how it's encrypted, and the passkey.

---

### Post by taikuodo on 2007-08-16
I think its reading my adapter, but its not seeing it in the wlan thing, watch this.

Bus 003 Device 001: ID 0000:0000
Bus 003 Device 003: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
**Bus 003 Device 002: ID 2001:3b00 D-Link Corp. [hex]**
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000 


but with the other thing it came out like this

[B]lo no wireless extensions.

eth0 no wireless extensions.

wlan0 no wireless extensions[/B]

Ill try reading your posts and unplugging the card and stuff.

---

### Post by cazique on 2007-09-04
i had the same problem here when i update from ubuntu 6 to ubuntu 7. 
The problem seemed, that **ndiswrapper and the acx-driver were loaded at the same time** and both tried to access the usb-device!! 

So here is what i did:
[SIZE="5"]
[COLOR="DarkRed"]1.) [/COLOR][/SIZE]**Go to /etc/modprobe.d/blacklist:**
```
sudo gedit /etc/modprobe.d/blacklist
```

[SIZE="5"][COLOR="DarkRed"]2.)[/COLOR][/SIZE] and add a new line: 
*"blacklist acx"*
[SIZE="5"]
[COLOR="DarkRed"]3.) [/COLOR][/SIZE]Then unplug the your d-link dwl-120+ usb wlan adapter.
[SIZE="5"][COLOR="DarkRed"]4.)[/COLOR] [/SIZE]**Remove the acx-driver:**
```
sudo rmmod acx
```

[SIZE="5"][COLOR="DarkRed"]5.)[/COLOR][/SIZE] **load the appropriate windowsdriver (included with the usb-adapter):**
```
sudo ndiswrapper -i windowsdriver.inf
```[SIZE="5"]
[COLOR="DarkRed"]6.)[/COLOR][/SIZE] **Check if everything went right and set the driver to auto-startup:**
```
ndiswrapper -l
ndiswrapper -m

```
[SIZE="5"]
[COLOR="DarkRed"]7.)[/COLOR][/SIZE] **Start your wlan:**
```
ifup wlan essid default
``` 
where 'default' is the you wlan-network-name. If you don't know it, just try 'default'.

[COLOR="DarkRed"]So that's what i had to do to get my d-link dwl-120+ usb wlan working again on ubuntu 7.04. It was fairly strange that it worked out of the box from the live cd ubuntu 6 but it wouldn't work anymore after the update to ubuntu 7. [/COLOR]

---

### Post by caricc on 2007-09-04
try copying the .inf & .sys file for the windows driver to your desktop in linux. then run ndiswrapper.  You may [HTML]http://ubuntuforums.org/showthread.php?t=527159[/HTML]
check out this thread and follow what kevdog told me to do . It should work.

---

