---
title: "Query regarding working/installing Lenovo Wireless Drivers"
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by adithya2 on 2013-10-04
I own Lenovo G570 laptop and I installed Ubuntu 12.10 (dual boot along with Windows).Everything works fine,but the Lenovo drivers for Bluetooth and WiFi are not available. Bluetooth and WiFi work only if they are enabled by launching the software that enables/disables the driver in windows.If I try to use the same in ubuntu ,it shows that it is software blocked.How to resolve this problem and how if possible to install drivers.
Regards and thanks in advance.

---

### Post by grahammechanical on 2013-10-04
Laptop manufacturers increase the battery usage time by switching stuff like wireless and bluetooth is if they are not required. Microsoft and Lenovo have worked together to give that functionality to the purchaser. But Lenovo have not worked with Linux developers to allow Linux distributions to do what the MIcrosoft OS can do. If we switch off adapter cards either by keyboard switch or by an OS, then those electronic cards/adapters remain off when we load another OS and that OS does not have the means to override what the other OS has done. This is life.

Regards.

---

### Post by Bucky Ball on 2013-10-04
*Thread moved to **Networking & Wireless**.*

Welcome. You may have more luck here. ***Installation & Upgrades*** is for installation and upgrades of the OS. ;)

Please open a terminal and input this command:
```

sudo lshw -C network
```

Post the output back here, thanks.

---

### Post by adithya2 on 2013-10-04
[COLOR=#000000]*-network [/COLOR]
[COLOR=#000000]description: Ethernet interface[/COLOR]
[COLOR=#000000]product: AR8152 v2.0 Fast Ethernet[/COLOR]
[COLOR=#000000]vendor: Atheros Communications[/COLOR]
[COLOR=#000000]physical id: 0[/COLOR]
[COLOR=#000000]bus info: pci@0000:07:00.0[/COLOR]
[COLOR=#000000]logical name: eth0[/COLOR]
[COLOR=#000000]version: c1[/COLOR]
[COLOR=#000000]serial: dc:0e:a1:61:ad:65[/COLOR]
[COLOR=#000000]capacity: 100Mbit/s[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/COLOR]
[COLOR=#000000]configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair[/COLOR]
[COLOR=#000000]resources: irq:44 memory:e0500000-e053ffff ioport:2000(size=128)[/COLOR]
[COLOR=#000000]*-network DISABLED[/COLOR]
[COLOR=#000000]description: Wireless interface[/COLOR]
[COLOR=#000000]product: AR9285 Wireless Network Adapter (PCI-Express)[/COLOR]
[COLOR=#000000]vendor: Atheros Communications Inc.[/COLOR]
[COLOR=#000000]physical id: 0[/COLOR]
[COLOR=#000000]bus info: pci@0000:08:00.0[/COLOR]
[COLOR=#000000]logical name: wlan0[/COLOR]
[COLOR=#000000]version: 01[/COLOR]
[COLOR=#000000]serial: 74:de:2b:d3:7d:17[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/COLOR]
[COLOR=#000000]configuration: broadcast=yes driver=ath9k driverversion=3.0.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn[/COLOR]
[COLOR=#000000]resources: irq:17 memory:e0400000-e040ffff[/COLOR]

---

### Post by Bucky Ball on 2013-10-05
```
broadcast=yes **driver=ath9k** driverversion=3.0.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
```

Driver installed. You should be good to go. When you left click the Network icon do you see available networks? Could you now post the output of:

```
iwconfig
```

Also, could you please explain this in a bit more detail?

[QUOTE=adithya2]Bluetooth and WiFi work only if they are enabled by launching the software that enables/disables the driver in windows.[/QUOTE]

Thanks.

---

### Post by adithya2 on 2013-10-05
I mean that if I boot up Windows 7 Ultimate and Software Enable the Wifi/Bluetooth Drivers,then the drivers can be detected in Ubuntu when the OS boots up,otherwise I am unable to access them if the Software Enable for WiFi/Bluetooth drivers are turned off.
CLI Output:> lo        no wireless extensions.

eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr off   Fragment thr off
          Power Management on
          
ppp0      no wireless extensions.




---

### Post by chili555 on 2013-10-05
I think Bucky and I would love to see this when the wireless is not working:```
rfkill list all
```

---

### Post by adithya2 on 2013-10-05
CLI Output for above command:
> 0: ideapad_wlan: Wireless LAN	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes




---

### Post by chili555 on 2013-10-06
Is there any change when you press the wireless combination, Fn+F2 or some such, and then run:```
rfkill list all
```It may take several tries as some key combinations are sequential, such as Off, Wireless on and Bluetooth off, both on, wireless off and bluetooth on, etc.

Is there any change with:```
sudo rfkill unblock all
rfkill list all
```How about with:```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
rfkill list all
```

---

### Post by divine shine on 2013-10-10
Heyy guys,

One of my friends had a similar problem after installing Ubuntu 13.04 yesterday on a Lenovo G560. I tried the ```
 rfkill unblock all 
```

The code managed to unblock the Bluetooth Driver's soft block.

But our problem here is that though we have the Wireless LAN hardware switch ON, the ```
 rfkill list all 
``` shows that the Wireless LAN is still hard blocked. We didn't find any change even after using the rfkill unblock all.

This is the output of <rfkill list all> before the unblock command :

[HTML]0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes
1: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
2: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
4: hci0: Bluetooth
Soft blocked: yes
Hard blocked: no[/HTML]

and this was the output of <rfkill list all> after the <rfkill unblock> command : 

[HTML]0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes
1: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
2: ideapad_bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
4: hci0: Bluetooth
Soft blocked: no
Hard blocked: no[/HTML]

 Please do try and sort this problem out for us.

 Thanks in advance.

---

### Post by adithya2 on 2013-10-11
Same problem here.Any replies in this aspect will be much appreciated and helpful.

---

