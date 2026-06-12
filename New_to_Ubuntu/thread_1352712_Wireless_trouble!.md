---
title: "Wireless trouble!"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by matt689 on 2009-12-11
Hello!  After successfully installing Ubuntu, I have run into my first problem.  I cannot view or connect to wireless networks.  I am currently connected via an Ethernet cord to my router, however this is not ideal for me.  My computer is a Dell Inspiron 1545 (I believe it has the dell wireless 1397).  I attempted the steps in the troubleshooting section on the help menu and made it to step 2 where it has me type in the command "sudo lshw -C network" and look for an output, along with the words "CLAIMED, UNCLAIMED, ENABLED or DISABLED." However I am not seeing any of these words to help me determine the status of the driver.  Here is my output:

> matt@matt-laptop:~$ sudo lshw -C network
[sudo] password for matt: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:05:09:e8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.105 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
matt@matt-laptop:~$ 

This is not my first attempt at Linux, however I have never made it past this stage.  I am determined to get it working this time though!  Any thoughts?

---

### Post by PRC09 on 2009-12-11
I have set up quite a few Dells with the following link.Connect with ethernet,do the updates and then check System>Administration>Hardware Drivers and see if the driver shows up.Then just activate and you should be good to go....

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by ublintu on 2009-12-12
you can check this as well (the second and the third posts) :
[http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom)
2 more ways...

---

### Post by woodnymph on 2009-12-12
also note the 4312 is only supported on 'g' networks, check your router.

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by bkratz on 2009-12-12
Here is how a fellow Dell user with the 1397  (BCM4312) solved his problems.

[http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom)

---

### Post by sandyd on 2009-12-12
you can either use bcm43xx-fwcutter
or install the driver that broadcom provides 
by running this....
32-bit
```

wget -c http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz
mkdir ~/build
mkdir ~/build/broadcom
mv hybrid*gz ~/build/broadcom/
cd ~/build/broadcom
make
sudo make install
sudo modprobe wl

```

64-bit
```

wget -c http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz
mkdir ~/build
mkdir ~/build/broadcom
mv hybrid*gz ~/build/broadcom/
cd ~/build/broadcom
make
sudo make install
sudo modprobe wl

```

---

