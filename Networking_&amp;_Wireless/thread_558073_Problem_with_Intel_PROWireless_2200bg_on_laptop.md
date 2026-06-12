---
title: "Problem with Intel PRO/Wireless 2200bg on laptop"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by straum on 2007-09-23
Hi.

I just installed ubuntu 7.04 on my fujitsu-siemens laptop and evrything except the wireless network works fine.
the wireless card is a Intel PRO/Wireless 2200bg and as far as I've read the drivers should be installed by default with ubuntu.

I think it has something to do with the 'wireless activate' button not working right and that the wireless card itself isn't activated.

I've tried the guide to activate it in my bios ([http://www.basementmedia.no/blogg.php?id=489](http://www.basementmedia.no/blogg.php?id=489))
but there's still no response from wireless.

also, output from iwconfig look like this:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

so.... i dont really know how to get it working.
hope someone can help me.

-straum

---

### Post by noob12 on 2007-09-24
Hi.  Yes your radio is disabled.  

What's the exact model of your Fujitsu-Siemens laptop?  The Lifebooks have pure hardware switches, generally sliders on the sides.  Just turn on.   The AMILOs require a kernel module to interpret the hotkey.   

The blog posting you pointed to says it works around this by enabling the wireless by default in the BIOS.  Are you saying that you upgraded your BIOS and set the wireless enabled in the new BIOS setting and the radio still isn't on?

Can you post the output of these commands:
```

uname -a

sudo lshw -C network

cat /sys/class/net/*/device/rf_kill

```

Can you see if this helps at all?
```

sudo modprobe -r ipw2200
sudo modprobe fsam7400 radio=1
sudo modprobe ipw2200

```

---

### Post by straum on 2007-09-24
Hi noob12 (no offense).

thanks for the help so far.

the out from the first code gave me this:
> uname -a
Linux cassander-laptop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux
**and** sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:28:94:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.19 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:e0200000-e0201fff irq:10
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@02:06.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:57:03:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: iomemory:e0203000-e0203fff irq:10

from that i can see you're right that the radio is turned off.

then i found that "sudo modprobe fsam7400 radio=1" changed it to:
 > sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:28:94:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.19 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:e0200000-e0201fff irq:10
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@02:06.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:57:03:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:e0203000-e0203fff irq:10

now im able to see the wireless networks, though the radio shuts down again when restart.
When i try to log on to a network it just keep trying to contact it (little icon spinning) without luck.

thanks again for the help so far.

-straum

---

### Post by noob12 on 2007-09-24
OK.

Run this.   It is adding a line that says "fsam7400 radio=1" to the file /etc/modules.  This tells the system to load that module on boot automatically with that option.  You only need to do this once.   

```

echo "fsam7400 radio=1" | sudo tee -a /etc/modules

```

This assumes the ipw2200 module doesn't need to be reloaded again after the radio is on.  I think it will work for you. 

Once you do that and reboot, see if the radio is on using the commands you used before.  If it is, and you are still unable to connect, then please post the output of these commands for more diagnosis:

```

cat /etc/network/interfaces

iwconfig

sudo iwlist scan

```

---

### Post by straum on 2007-09-24
ok.

echo gave me the radio from restart, but still no dice trying to connect.

cat /etc.... gave me:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

and iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and finally sudo iwlist scan:
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:51:6D:F6:5D
                    ESSID:"musik"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-78 dBm  
                    Extra: Last beacon: 296ms ago
          Cell 02 - Address: 00:17:9A:84:FC:E7
                    ESSID:"mortensen"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:13
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-36 dBm  
                    Extra: Last beacon: 112ms ago
                    Extra: Channel flags: INVALID 

mmmh... can you read any of this?

thx again again
-straum

---

### Post by noob12 on 2007-09-24
Yes, it's very useful.  Your radio is working now and scanning local nets.

Are any of the access points ("musik" or "mortenson") yours?  If so, which one?

Is the ESSID broadcast enabled on the access point to which you wish to connect?  If not, I suggest you enable it.   (Once you are able to connect, I suggest you enable WPA on your router and connect using a key, but it's often easier to start with encryption off as you have it now.)

In order for Network Manager to manage the connections entirely, you should go into "System | Administration | Network" and select your wireless interfaces and Properties and put it into "roaming mode".  Do the same for the wired.

Optionally:  You can also edit your /etc/network/interfaces file using the command **sudo gedit /etc/network/interfaces**.  You can remove the sections for everything except the first one:  lo (loopback).  Keep that one (!)  Save the file and exit.

Try enabling wireless by right-clicking on the Network Manager (NM) icon and selecting Enable Wireless.  Then left click on it and select the AP you wish to connect to.

---

### Post by straum on 2007-09-27
The network problem is fixed now! thanks for the help!  

It was just the "musik" and "mortenes" I couldn't join because they were password protected. 
so again thanks for the help! I'm not really sure what got it working, but it is working now.

---

