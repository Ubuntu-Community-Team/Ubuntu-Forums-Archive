---
title: "wireless drivers not working: ubuntu 17.10"
date: 2018-03-29
forum: Networking &amp; Wireless
---

### Post by eth0s2 on 2018-03-29
Hey all.hoping to get some help here. I Just installed ubuntu on an hp stream laptop and im having issues with the wireless card. the in board card is a realtek c822. i found a thread on bug reports from january about it not being supported. found the manufacturer's driver for linux but the install process is well above my level without some help. it has you reassigning dns ip's, etc. currently have internet access through my phone on the machine. I'm still somewhat new to Linux and loving it, on my other laptop the installation was seamless i had no problems. This is admittedly frustrating. I went and bought a netgear AC600 usb card to see if that would work. Went to the software and updates gui and told it to run the third party driver for it. Had to bypass secure boot and it now shows the driver is there, but it's not working either. if support for the realtek inboard card is available, id prefer to have it working, but either it or the usb adapter is fine as long as i get it up and running. here's the output of sudo lshw -c network

```
drew@DrewsMachine:~$ sudo lshw -c network
  *-network UNCLAIMED       
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:1000(size=256) memory:91000000-9100ffff
  *-network:0
       description: Ethernet interface
       physical id: 3
       bus info: usb@1:2
       logical name: enp0s20u2c4i2
       serial: b6:9c:df:6a:7e:e5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth ip=172.20.10.3 link=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 4
       logical name: bnep0
       serial: 2c:6f:c9:1c:ae:54
       capabilities: ethernet physical
       configuration: broadcast=yes ip=172.20.10.2 multicast=yes
drew@DrewsMachine:~$ 

```
 and sudo lsusb:

```
drew@DrewsMachine:~$ sudo lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b00b Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05c8:022a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 005: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 001 Device 002: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
drew@DrewsMachine:~$ 

```
thanks in advance!

---

### Post by eth0s2 on 2018-03-31
did i do something wrong here?

---

### Post by praseodym on 2018-03-31
Install the driver for the stick via

```
sudo apt-get install dkms build-essential rtl8812au-dkms
```
Reboot.

---

### Post by praseodym on 2018-03-31
Please also run the wireless script from the sticky thread and show the outputs

---

### Post by eth0s2 on 2018-03-31
drew@DrewsMachine:~$ sudo apt-get install dkms build-essential rtl8812au-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.4ubuntu1).
dkms is already the newest version (2.3-3ubuntu3).
rtl8812au-dkms is already the newest version (4.3.8.12175.20140902+dfsg-0ubuntu7).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by jeremy31 on 2018-03-31
See the wireless script link in my signature and post results, also post results for ```
mokutil --sb-state
```

---

### Post by eth0s2 on 2018-03-31
```
 drew@DrewsMachine:~$ mokutil --sb-state
SecureBoot enabled


```

---

### Post by eth0s2 on 2018-03-31
got this one fixed. thanks guys!

---

### Post by jeremy31 on 2018-03-31
Fixed on irc #ubuntu with commands from [https://gist.github.com/jeremyb31/8687eec6ea7f9dca9e71a24aab197f0e](https://gist.github.com/jeremyb31/8687eec6ea7f9dca9e71a24aab197f0e)
[https://gist.github.com/jeremyb31/e08fe3f177eea0cb623d0f9c4f554339](https://gist.github.com/jeremyb31/e08fe3f177eea0cb623d0f9c4f554339)
And getting Secure Boot disabled

---

