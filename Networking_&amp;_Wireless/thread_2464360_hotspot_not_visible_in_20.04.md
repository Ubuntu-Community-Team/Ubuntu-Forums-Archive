---
title: "hotspot not visible in 20.04"
date: 2021-06-30
forum: Networking &amp; Wireless
---

### Post by akashsinhaha on 2021-06-30
worked fine for two days after which no devices are showing in Visible Networks of wifi setting

---

### Post by dddman on 2021-06-30
Try reinstalling your hotspot

This works in 20.04
[https://ubuntuhandbook.org/index.php/2019/10/fix-wi-fi-hotspot-not-working-ubuntu-18-04/](https://ubuntuhandbook.org/index.php/2019/10/fix-wi-fi-hotspot-not-working-ubuntu-18-04/)

Additional reading
[https://askubuntu.com/questions/1230690/wifi-hotspot-option-disabled-after-upgrade-to-ubuntu-20-04](https://askubuntu.com/questions/1230690/wifi-hotspot-option-disabled-after-upgrade-to-ubuntu-20-04)

---

### Post by akashsinhaha on 2021-07-01
Sorry but what i mean is that my laptop is not showing my mobile's hotspot name in visible networks of wifi settings. 
I want to connect my laptop to my mobile hotspot and not to create a hotspot using my laptop.

---

### Post by dddman on 2021-07-01
Oh...
That's how I also hook up to the internet.  At times I need to reboot my phone so the connection will show up.  Have you tried that?  And there are times when a reboot of ubuntu NetworkManager is necessary, even though it refreshes itself.  That's all I have

---

### Post by akashsinhaha on 2021-07-02
yeah sometimes when I restart my Laptop it starts working but again after 1 to 3 hours it stops. And its a pain to restart the laptop everytime this happens. I will try rebooting the network manager and report.

---

### Post by dddman on 2021-07-02
> **akashsinhaha said:**
> I will try rebooting the network manager and report.
There are different ways of doing this
[https://linuxconfig.org/how-to-restart-network-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-restart-network-on-ubuntu-18-04-bionic-beaver-linux)
I'm on a virtual system and cannot test the different methods.

---

### Post by akashsinhaha on 2021-07-03
Thanks I will try these and see if something works

---

### Post by akashsinhaha on 2021-07-04
> **dddman said:**
> There are different ways of doing this

none worked for me

---

### Post by dddman on 2021-07-05
Is your driver up to date?

```
sudo lshw -C network && inxi -n
```

Open Software Updater and go to Settings>Drivers.  That will check for drivers.

Also check syslog for any clues
```
cat /var/log/syslog
```

And there is this
[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-find.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-find.html.en)

I currently have nothing else to offer :(

---

### Post by akashsinhaha on 2021-07-05
here is what i got from 
```
 [COLOR=#000000][FONT=&quot]sudo lshw -C network && inxi -n 
```

[/FONT][/COLOR]*-network                 
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: 14:58:d0:ca:fc:ff
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-59-generic firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 ioport:4000(size=256) memory:b5500000-b5500fff memory:b5400000-b5403fff
  *-network
       description: Ethernet interface
       physical id: 3
       bus info: usb@2:1
       logical name: usb0
       serial: 4a:9d:4c:20:ce:4e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.5 link=yes multicast=yes
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169 
  IF: enp8s0 state: down mac: 14:58:d0:ca:fc:ff 
  IF-ID-1: usb0 state: unknown speed: N/A duplex: N/A mac: 4a:9d:4c:20:ce:4e 
[COLOR=#000000][/COLOR]

---

