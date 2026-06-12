---
title: "Liksys WRT54GS + wireless laptop configuration"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Walc on 2008-04-18
Hello guys
I just bought myself a Linksys WRT54GS router.
I have 1 computer with vista onboard and a hp compaq nx7400 laptop with ubuntu 7.10 onboard.
now i have managed to set up internet on my desktop vista pc <ethernet> now the thing is id like to set up wireless connection for that laptop.
Just to let u know i have never dealt with setting up wireless connection b4 ;)

as for settings: i havent set up wirelesss security yet, the 'wireless - g /wlan led is lit .

thx in advance i hope i can get this set up :)

---

### Post by dstew on 2008-04-18
The setup window is System --> Administration --> Network. Your wireless adapter should show up there. Click on it, and then click Properties. Set it up the way your router is set up (usually to get IP address automatically by DHCP), and enter encryption type and your wireless key (if you are using encryption.) After that, go back to the tab and check Enable and it should connect.

---

### Post by Walc on 2008-04-18
thin is....
look like theres no wireless connection detected...
all i canb see there is:

[*]wired connection

[*]modem connection

both are 'grey' ..seems inactive 

?


how can i check wheter my wireless card on laptop is enabled? maybe thaats the issure here

---

### Post by dstew on 2008-04-18
Open a terminal window (Applications --> Accessories --> Terminal) and on the command line enter```
lspci
```That should list the PCI hardware, including your wireless adapter. Post the output to the forum.

---

### Post by Walc on 2008-04-18
```

robert@lapek:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
robert@lapek:~$ 

```

---

### Post by dstew on 2008-04-18
Looks like your wireless card is an Intel 3945ABG. Post the output of ```
iwconfig
sudo lshw -C network
```

---

### Post by Walc on 2008-04-18
```

robert@lapek:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

robert@lapek:~$ sudo lshw -C network
[sudo] password for robert:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:17:08:2d:bb:a3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
robert@lapek:~$ 

```

---

### Post by dstew on 2008-04-18
It looks like your wireless adapter is operating, but it has no logical interface name. Post the output of```
cat /etc/network/interfaces
```EDIT: Also, try this```
sudo modprobe -r ipw3945
sudo modprobe ipw3945
```Those commands unload and reload the driver. Then do iwconfig again and see if it shows up.

---

### Post by Walc on 2008-04-18
```

robert@lapek:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 

robert@lapek:~$ sudo modprobe -r ipw3945 
[sudo] password for robert: 
robert@lapek:~$ sudo modprobe ipw3945 
robert@lapek:~$ 

```


thank u dtev for helpin me out

```

iwconfig >>>>>

robert@lapek:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

system> administration > newtowrk: still got 2 options there, no wireless tho :P

im thinking maybe i did sth wrong installing the router onto desktop pc.....but then again i can see the wlan led it lit.....

---

### Post by dstew on 2008-04-18
> im thinking maybe i did sth wrong installing the router onto desktop pcNo, it is not a router problem. For some reason the driver is not able to create a logical interface for the card. It might be possible to use the Windows driver with ndiswrapper. I am not sure what the problem is.

---

### Post by Walc on 2008-04-18
maybe i should update router drivers?...or a firmware

---

### Post by Walc on 2008-04-18
[[IMG]http://img213.imageshack.us/img213/5510/screenshotnx3.th.png[/IMG]](http://img213.imageshack.us/my.php?image=screenshotnx3.png)

[[IMG]http://img213.imageshack.us/img213/2194/screenshot1bl4.th.png[/IMG]](http://img213.imageshack.us/my.php?image=screenshot1bl4.png)

[[IMG]http://img219.imageshack.us/img219/4549/screenshot2vt1.th.png[/IMG]](http://img219.imageshack.us/my.php?image=screenshot2vt1.png)

[[IMG]http://img230.imageshack.us/img230/6127/screenshot3fq0.th.png[/IMG]](http://img230.imageshack.us/my.php?image=screenshot3fq0.png)


The thing is.... i can finally see some data in the dns and hosts tab....
just wondering is it partially working, or these r just leftovers from my old modem cable connection? <with the same isp>

---

### Post by Walc on 2008-04-19
bump?

---

