---
title: "Wireless, ACX 100 driver installation"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by QliMZ on 2008-07-15
Hi,

I'm 15 and i never used a linx system before, so this is my first time using ubuntu, i installed it, with windows xp, so i have a dual boot. Everything went fine but i can't connect to my wireless connection, so i browsed around on these forums and did iwconfig, and it said my wireless connection isn't supported, or something like that. So I downloaded and extracted the driver on ubuntu, now is my question how can i install this driver easily, cause i am not experienced with this.

Thanks alot !

---

### Post by chili555 on 2008-07-15
Are you sure the built-in module, *acx* won't work? Open a terminal and do:```
sudo modprobe acx
iwconfig
```Does your wireless card show up? If not, please post:```
dmesg | grep acx
sudo lshw -C network
```Thanks.

---

### Post by QliMZ on 2008-07-15
sudo modprobe acx
```
l0 no wireless extensions.
eth0 no wireless extensions.
```

dmesg | grep acx
```
acx: Loaded combined PCI/usb driver, firmware_ver=default
acx: compiled to use 32bit I/O acces
acx: found ACX100-based wireless network card at 0000:00:0a.0
acx: loading firmware for acx100 chipset with radio ID 0D
acx: FIRMWARE IMAGE 'ACX/DEFAULT/TIACX100C0D' WAS NOT PROVIDED. CHECK YOUR HOTPLUG SCRIPTS.
```
( I shortened it, cause i'm on a laptop typing this, and i type the possible error for my problem in caps, i think that is causing this.)

sudo lshw -C network
```
network:0
description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems
physical id: 4
logical name: eth0
version: 91
...

network:1
description: Wireless interface
product: ACX 100 22Mbps Wireless Interface
vendor: Texas Instruments
physical id: a
version: 00
width: 32 bits
configuration: boardcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 902.11b
```

I left some things out, let me know if i need to do something else, hope this will be fixed soon, ...
Thx

---

### Post by chili555 on 2008-07-15
Do you actually have the firmware, which is included in *linux-restricted-modules*? Check to see if:```
locate acx | grep firmware
```produces many lines like:> /lib/firmware/2.6.24-19-generic/acx/default/tiacx100usb
/lib/firmware/2.6.24-19-generic/acx/default/tiacx111c16
/lib/firmware/2.6.24-19-generic/acx/default/tiacx111c17
/lib/firmware/2.6.24-19-generic/acx/default/tiacx111c19If not, please:```
sudo apt-get install linux-restricted-modules-generic
```

A well known issue is that, all though *dmesg* complains it can't load the firmware, it actually loads a few lines later! Check here: [http://ubuntuforums.org/showthread.php?p=3375718](http://ubuntuforums.org/showthread.php?p=3375718)

Were there any *acx* entries further along in *dmesg* beyond what you posted?

---

### Post by QliMZ on 2008-07-15
This is the full log:

```
alexander@qlimzdesktop:~$ sudo modprobe acx
alexander@qlimzdesktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=15/100  Signal level=26/100  Noise level=16/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:44  Invalid misc:0   Missed beacon:0

alexander@qlimzdesktop:~$ dmesg | grep acx
[   33.273985] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   33.273993] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   33.274139] acx: found ACX100-based wireless network card at 0000:00:0a.0, irq:20, phymem1:0xCFFFD000, phymem2:0xCFFE0000, mem1:0xe095c000, mem1_size:4096, mem2:0xe0a20000, mem2_size:65536
[   33.275148] acx: loading firmware for acx100 chipset with radio ID 0D
[   37.531612] acx: firmware image 'acx/default/tiacx100c0D' was not provided. Check your hotplug scripts
[   38.285912] acx: loading radio image for radio 0D
[   38.801042] acx: === chipset TNETW1100B, radio type 0x0D (Maxim), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.9.8.b' ===
[   38.801432] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.24-19-generic
[   38.801494] usbcore: registered new interface driver acx_usb
alexander@qlimzdesktop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0a:e6:ad:1c:32
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wlan0
       version: 00
       serial: 00:0d:88:8b:2a:54
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+
alexander@qlimzdesktop:~$ 



```

---

### Post by chili555 on 2008-07-15
So, your interface is working! Can you now click the little Network Manager icon and connect?

---

### Post by QliMZ on 2008-07-15
Well the problem is, my wireless connection is in the list, so i click it and then i have to enter my password. My connection on windows is installed as a WeP, so i entered my password as a wep to, but that doesn't work, and when i try entering it as a leap the connection symbol dissapears and ubuntu starts freezing, like firefox doesn't work and other programs to, like shutdown comes really late or just freezes.

---

### Post by chili555 on 2008-07-15
I believe there is a drop-down for '40-128 bit hexadecimal.' Please try your WEP key there. I assume it's a 10- or 26-character key?

---

### Post by QliMZ on 2008-07-15
When i connect with my wep key, the network icon just dissapears, and when i click firefox then it freezes everytime.

---

### Post by QliMZ on 2008-07-15
[[IMG]http://img410.imageshack.us/img410/4879/screenshot1qp3.th.png[/IMG]](http://img410.imageshack.us/my.php?image=screenshot1qp3.png)

After that, the icon disappears, and firefox is really slow and then freezes, jsut like pidgin and some other programs.

---

### Post by chili555 on 2008-07-15
Well, I doubt this is an acx driver problem. The icon should not disappear, it should change into five rising bars and a pop-up should say you are connected. Let's take Network Manager out of the mix. Please do:```
sudo iwconfig wlan0 essid <your_router's essid>
sudo iwconfig wlan0 key <your_hex_key>
sudo dhclient wlan0
```Do you connect?

You might open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you try Firefox and see what the kernel is alarmed about as it freezes.

---

### Post by QliMZ on 2008-07-15
Hmm..I don't have an Essid ?

---

### Post by chili555 on 2008-07-15
> **QliMZ said:**
> Hmm..I don't have an Essid ?Hmmmmm...I wonder if it might be WiFi1830. Check what identifier, or essid, your router is broadcasting with:```
sudo iwlist wlan0 scan
```

---

### Post by QliMZ on 2008-07-15
I'm getting this:
```
Jul 15 20:28:41 qlimzdesktop kernel: [  165.455767] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)

```

---

### Post by chili555 on 2008-07-15
Please try these:```
sudo iwconfig wlan0 essid <your_router's essid>
sudo iwconfig wlan0 key <your_hex_key>
sudo iwconfig wlan0 rate auto
sudo dhclient wlan0
```

---

### Post by jingo811 on 2008-07-15
> **QliMZ said:**
> Hmm..I don't have an Essid ?
If you have admin access to you home's router then you can check what ESSID it has.  Else you could dualboot into your Windows partition and see if you can find your router's ESSID there.

>  -- maybe MAC filtering by peer?)
I might be wrong here but does your Wireless NIC work in Windows or haven't you tried it yet?

---

### Post by QliMZ on 2008-07-16
I just woke up, i'm going to setup my mac adress on my routers page and see if that works, and then i will try

```
sudo iwconfig wlan0 essid <your_router's essid>
sudo iwconfig wlan0 key <your_hex_key>
sudo iwconfig wlan0 rate auto
sudo dhclient wlan0
```

---

### Post by QliMZ on 2008-07-16
Didn't work, this is what i got

```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0d:88:8b:2a:54
Sending on   LPF/wlan0/00:0d:88:8b:2a:54
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.4 from 192.168.1.1
DHCPREQUEST of 192.168.1.4 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.4 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.1
egrep: /etc/resolv.conf: No such file or directory
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.4 -- renewal in 68951 seconds.
```

---

### Post by QliMZ on 2008-07-16
Ok, i managed to connect to the wireless network, but i don't see bars with my connection signal, o only see 2 televisions and it says that i am manual connected, is this ok, or must i change this. ?

---

### Post by chili555 on 2008-07-16
> it says that i am manual connected, is this ok, or must i change this. ?If you want to use your computer to roam to the coffee shop, library and university hotspot, then we do need to fix this.

If yours is a stay-at-home computer, then we can put all these details in */etc/network/interfaces* and it will connect correctly on boot.

What's your preference?

---

### Post by razmakati on 2008-12-08
Sorry to dredge this post from the depths. I have run into the same problem as the OP. On my laptop I can get it connected with these commands but i have to keep re entering them everytime i start it. 

sudo iwconfig wlan0 essid <your_router's essid>
sudo iwconfig wlan0 key <your_hex_key>
sudo iwconfig wlan0 rate auto
sudo dhclient wlan0

what can i do to make sure it starts automatically

all my outputs are identical to the op

if you can help thanks a bunch

---

