---
title: "Strange iwconfig output"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by undercovapenguin on 2008-02-24
I have a dual-boot system running Windows XP and Ubuntu 7.10. I have an ipw3945 wireless card. When I first installed Ubuntu my wireless worked perfectly however, I must have done something because now it doesn't work. Iwconfig returns:
 lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
          
rtap0     no wireless extensions.

I think it may be to do with monitor mode however all attempts to change it to managed make no difference. Any help would be greatly appreciated, thanks.

---

### Post by undercovapenguin on 2008-02-25
Any help here???

---

### Post by Junglizer on 2008-02-25
It just mean's you haven't associated eth1 with any access point. You need to tell it to connect to what ever your wireless AP is named.

```
iwconfig eth1 essid "<insert_AP_name_here>"
```

---

### Post by Junglizer on 2008-02-25
Also, you may need to change it back to managed mode, since it is currently listed as being in rfmon. So you might need: ```
iwconfig eth1 mode Managed
```

---

### Post by undercovapenguin on 2008-02-25
When i try to set the essid it returns: Operation not supported. Any suggestions? Thanks so much for the help.

---

### Post by undercovapenguin on 2008-02-25
I looked at another thread and ran this:

```
@ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:2e:d2:2b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical wireless
       configuration: broadcast=yes driver=ipwraw driverversion=1.2.2k  -  ipwraw-ng v2.0.0 09070.0 0:0 () firmware=0.0 0:0 () latency=0 link=no module=ipwraw multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0f:23:57
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.100.18 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
```

Anybody know how to enable my wireless? Thanks

---

### Post by ninja nicco on 2008-04-16
It seams that you have the driver "ipwraw" enabled. This is not default and it could help to change it back to the ipw3945 driver by disabling the ipwraw driver:
```

sudo modprobe -r ipwraw

```
and enabling the usual one:
```

sudo modprobe ipw3945

```



You could also try to run
```

sudo ifconfig 'device_name'(in you case 'eth1') up

```
to be sure the devise is enabled.



When you have the device running with the right driver you just run:
```

sudo iwconfig 'device_name' mode managed essid 'network_name' key s:'your_ascii_pasphrase'

```
to connect to your wireless network.

---

### Post by chili555 on 2008-04-16
NetworkManager will not connect wireless if you have wired available, which you do:```
ip=192.168.100.18 latency=64 link=yes
```I would disconnect the wire and then do:```
sudo ifconfig eth0 down
```Then return to your wireless stuff.

---

