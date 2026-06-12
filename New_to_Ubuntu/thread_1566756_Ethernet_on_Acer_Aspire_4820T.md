---
title: "Ethernet on Acer Aspire 4820T"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Melite on 2010-09-02
I am running Ubuntu 10.04 on my Acer Aspire 4820T laptop alongside Windows 7. Not surprisingly, I can't get my ethernet connection (let alone wireless) to work.

I have looked at the general thread on problems with the Acer 4820 ([http://microsoft_rules.ubuntuforums.org/showthread.php?t=1495123&highlight=acer+4820+internet](http://microsoft_rules.ubuntuforums.org/showthread.php?t=1495123&highlight=acer+4820+internet)) but as I'm very new to Linux I have not managed to fix this yet.

I have tried the following:

Downloading the "AR81Family Linux Driver" from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (specifically, v1.0.1.13) on a different laptop, transferred it to the Acer and tried installing it using

```


tar zxvf AR81Family-Linux-v1.0.1.13.tar.gz
sudo su
apt-get install build-essential
apt-get install linux-generic-header
make install
modprobe atl1e

```Which resulted in:

```

emma@emma-laptop:~/Bureaublad$ tar zxvf AR81Family-linux-v1.0.1.13.tar.gz
./atl1e.7
./atl1e.spec
./at_osdep.h
./copying
./dkms.conf
./ldistrib.txt
./Makefile
./pci.updates
./readme
./release_note.txt
./src/
./src/atl1c.h
./src/atl1c_ethtool.c
./src/atl1c_hw.c
./src/atl1c_hw.h
./src/atl1c_main.c
./src/atl1c_param.c
./src/atl1e.h
./src/atl1e_ethtool.c
./src/atl1e_hw.c
./src/atl1e_hw.h
./src/atl1e_main.c
./src/atl1e_param.c
./src/at_common.h
./src/at_common_main.c
./src/at_osdep.h
./src/kcompat.c
./src/kcompat.h
./src/kcompat_ethtool.c

gzip: stdin: decompression OK, trailing garbage ignored
./src/Makefile
./src/Module.markers
./src/Module.symvers
./src/modules.order
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

```The next two steps are not working either:

```

root@emma-laptop:/home/emma/Bureaublad# apt-get install build-essential
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
E: Kon pakket build-essential niet vinden

root@emma-laptop:/home/emma/Bureaublad# apt-get install linux-generic-header
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
E: Kon pakket linux-generic-header niet vinden

```(Translates as: could not find package so-and-so). 

What am I doing wrong?

I have looked at other solutions, but most require at least a wired connection. I would really appreciate it if someone could help me with this.

Thanks in advance.

---

### Post by Cypress421 on 2010-09-02
Enter this into a terminal:

sudo lshw -C network

Make sure wireless is enabled. What do you see?

---

### Post by Melite on 2010-09-03
Thanks for replying!

It gives me:

```

  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: c8:0a:a9:ac:e5:50
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1C driverversion=1.0.1.13 firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:33 memory:d3400000-d343ffff ioport:2000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d2400000-d2403fff

```

---

### Post by Cypress421 on 2010-09-05
You can follow the instructions here:
 
[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)
 
You need to find the Windows driver for your wireless card, and then find the relevant .inf file. Once you've found the driver, use Universal Extractor to extract the driver. Install UE, then right click the .exe and extract to the folder. In that folder you'll find an .inf file that you need. If the driver is a .zip file, you don't need UE.

---

