---
title: "Wireless problem"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by jtb108 on 2007-05-19
Hello,

I posted about a wireless problem a few weeks ago.  I received a lot of advice from people who are helpful and know Ubuntu much better than I do.   However, I could not fix the problem.

I used wireless easily in Edgy Eft.  I did the upgrade to Feisty Fawn and now Ubuntu won't give me the wireless option under Network Manager.

I looked at a trouble-shooting guide at  
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

and I am showing the results of those steps in hopes that this information my help someone help me.

.

~$ lspci


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller



Then a statement on the website said    "Look at the output of the messages as you insert the PCMCIA card. Something should happen. You should be able to see that the drivers are loaded or a statement that the driver is already loaded"  so I typed:

$ tail -f /var/log/messages


May 19 19:01:06 john192-laptop kernel: [  217.352000] Bluetooth: RFCOMM ver 1.8
May 19 19:01:09 john192-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May 19 19:01:09 john192-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May 19 19:01:18 john192-laptop gconfd (john192-7277): starting (version 2.18.0.1), pid 7277 user 'john192'
May 19 19:01:18 john192-laptop gconfd (john192-7277): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 19 19:01:18 john192-laptop gconfd (john192-7277): Resolved address "xml:readwrite:/home/john192/.gconf" to a writable configuration source at position 1
May 19 19:01:18 john192-laptop gconfd (john192-7277): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 19 19:01:18 john192-laptop gconfd (john192-7277): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 19 19:01:18 john192-laptop gconfd (john192-7277): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 19 19:01:24 john192-laptop gconfd (john192-7277): Resolved address "xml:readwrite:/home/john192/.gconf" to a writable configuration source at position 0
^[[B



Then I ran the following

$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I would appreciate any help with this.  I am lost.  I can log on from a wired network without any trouble and I am using a dual-boot system.  My wireless card works under Windows but I would much rather be safe with Ubuntu,

Thank,

John B.

---

### Post by chili555 on 2007-05-20
Did you install *linux-restricted-modules-generic*? Your ipw3945 should spring to life! Also, be sure the wireless switch on your laptop, if there is one, is on.

---

### Post by jtb108 on 2007-05-20
Thank you for your response.

According to Synaptic Package Manager the following are installed:

linux restricted modules 2.61, 2.6.17,7-10.1
linux restricted modules 2.61, 2.6.17,7-11.2
linux restricted modules 2.62(2.6.20.5-15.20
linux restricted modules com 2.6.20 5-15.20
linux restricted modules generic 2.6.20.15.14

Please let me know if this helps.

Thanks again,

John B.

---

### Post by chili555 on 2007-05-20
Please let us see the results of:```
sudo lshw -C network
cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
```Thanks.

---

### Post by jtb108 on 2007-05-20
Hello,

I ran the command and got the following:

sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:a0:d1:62:3d:07
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-5 ip=10.71.0.173 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d6000000-d601ffff ioport:2000-201f irq:17
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:da000000-da000fff irq:18
john192@john192-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:a0:d1:62:3d:07
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-5 ip=10.71.0.173 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d6000000-d601ffff ioport:2000-201f irq:17
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:da000000-da000fff irq:18

Then I tried the following:


john192@john192-laptop:~$ cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
cat: /sys/bus/pci/drivers/ipw3945/0000:05:00.0/rf_kill: Resource temporarily unavailable

I tried it again about 2 minutes later.

john192@john192-laptop:~$ ~$ sudo lshw -C network
bash: ~$: command not found
john192@john192-laptop:~$ Password:
bash: Password:: command not found
john192@john192-laptop:~$   *-network               
bash: *-network: command not found
john192@john192-laptop:~$        description: Ethernet interface
bash: description:: command not found
john192@john192-laptop:~$        product: 82573L Gigabit Ethernet Controller
bash: product:: command not found
john192@john192-laptop:~$        vendor: Intel Corporation
bash: vendor:: command not found
john192@john192-laptop:~$        physical id: 0
bash: physical: command not found
john192@john192-laptop:~$        bus info: pci@02:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
Make sure you have the 'universe' component enabled
bash: bus: command not found
john192@john192-laptop:~$        logical name: eth0
bash: logical: command not found
john192@john192-laptop:~$        version: 00
bash: version:: command not found
john192@john192-laptop:~$        serial: 00:a0:d1:62:3d:07
bash: serial:: command not found
john192@john192-laptop:~$        size: 100MB/s
bash: size:: command not found
john192@john192-laptop:~$        capacity: 1GB/s
bash: capacity:: command not found
john192@john192-laptop:~$        width: 32 bits
bash: width:: command not found
john192@john192-laptop:~$        clock: 33MHz
bash: clock:: command not found
john192@john192-laptop:~$        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
bash: capabilities:: command not found
john192@john192-laptop:~$        configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-5 ip=10.71.0.173 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
bash: configuration:: command not found
john192@john192-laptop:~$        resources: iomemory:d6000000-d601ffff ioport:2000-201f irq:17
bash: resources:: command not found
john192@john192-laptop:~$   *-network
bash: *-network: command not found
john192@john192-laptop:~$        description: Network controller
bash: description:: command not found
john192@john192-laptop:~$        product: PRO/Wireless 3945ABG Network Connection
bash: product:: command not found
john192@john192-laptop:~$        vendor: Intel Corporation
bash: vendor:: command not found
john192@john192-laptop:~$        physical id: 0
bash: physical: command not found
john192@john192-laptop:~$        bus info: pci@05:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
Make sure you have the 'universe' component enabled
bash: bus: command not found
john192@john192-laptop:~$        version: 02
bash: version:: command not found
john192@john192-laptop:~$        width: 32 bits
bash: width:: command not found
john192@john192-laptop:~$        clock: 33MHz
bash: clock:: command not found
john192@john192-laptop:~$        capabilities: bus_master cap_list
bash: capabilities:: command not found
john192@john192-laptop:~$        configuration: driver=ipw3945 latency=0
bash: configuration:: command not found
john192@john192-laptop:~$        resources: iomemory:da000000-da000fff irq:18
bash: resources:: command not found
john192@john192-laptop:~$ john192@john192-laptop:~$ sudo lshw -C network
bash: john192@john192-laptop:~$: command not found
john192@john192-laptop:~$   *-network               
bash: *-network: command not found
john192@john192-laptop:~$        description: Ethernet interface
bash: description:: command not found
john192@john192-laptop:~$        product: 82573L Gigabit Ethernet Controller
bash: product:: command not found
john192@john192-laptop:~$        vendor: Intel Corporation
bash: vendor:: command not found
john192@john192-laptop:~$        physical id: 0
bash: physical: command not found
john192@john192-laptop:~$        bus info: pci@02:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
Make sure you have the 'universe' component enabled
bash: bus: command not found
john192@john192-laptop:~$        logical name: eth0
bash: logical: command not found
john192@john192-laptop:~$        version: 00
bash: version:: command not found
john192@john192-laptop:~$        serial: 00:a0:d1:62:3d:07
bash: serial:: command not found
john192@john192-laptop:~$        size: 100MB/s
bash: size:: command not found
john192@john192-laptop:~$        capacity: 1GB/s
bash: capacity:: command not found
john192@john192-laptop:~$        width: 32 bits
bash: width:: command not found
john192@john192-laptop:~$        clock: 33MHz
bash: clock:: command not found
john192@john192-laptop:~$        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
bash: capabilities:: command not found
john192@john192-laptop:~$        configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-5 ip=10.71.0.173 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
bash: configuration:: command not found
john192@john192-laptop:~$        resources: iomemory:d6000000-d601ffff ioport:2000-201f irq:17
bash: resources:: command not found
john192@john192-laptop:~$   *-network
bash: *-network: command not found
john192@john192-laptop:~$        description: Network controller
bash: description:: command not found
john192@john192-laptop:~$        product: PRO/Wireless 3945ABG Network Connection
bash: product:: command not found
john192@john192-laptop:~$        vendor: Intel Corporation
bash: vendor:: command not found
john192@john192-laptop:~$        physical id: 0
bash: physical: command not found
john192@john192-laptop:~$        bus info: pci@05:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
Make sure you have the 'universe' component enabled
bash: bus: command not found
john192@john192-laptop:~$        version: 02
bash: version:: command not found
john192@john192-laptop:~$        width: 32 bits
bash: width:: command not found
john192@john192-laptop:~$        clock: 33MHz
bash: clock:: command not found
john192@john192-laptop:~$        capabilities: bus_master cap_list
bash: capab.ilities:: command not found
john192@john192-laptop:~$        configuration: driver=ipw3945 latency=0
bash: configuration:: command not found
john192@john192-laptop:~$        resources: iomemory:da000000-da000fff irq:18
bash: resources:: command not found
john192@john192-laptop:~$ john192@john192-laptop:~$ cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
bash: john192@john192-laptop:~$: command not found
john192@john192-laptop:~$ cat: /sys/bus/pci/drivers/ipw3945/0000:05:00.0/rf_kill: Resource temporarily unavailable
bash: cat:: command not found


Hopefully this makes sense to you.

Thanks,

John B

---

### Post by chili555 on 2007-05-21
You are an enthusiastic copy-n-paster! The command is:```
cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
```It is *not:*```
john192@john192-laptop:~$ cat /sys/bus/pci/drivers/ipw3945/*/rf_kill
```Which is what you pasted after your command prompt. It even told you: *john192@john192-laptop:~$: command not found*

When you see 'command not found,' a probable cause is that you've mistyped or misspelled a command. I've done it myself, often! Stop and recheck your work before you proceed.

Please open System -> Administration -> Restricted Drivers Manager and be sure the Intel 3945 driver is checked. It may tell you to reboot if you enable it.

Next, try:```
sudo ifconfig eth1 up
```Let us know the results. Thanks.

---

