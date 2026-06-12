---
title: "TP Link T2UHP not working under kernel 4.20"
date: 2019-01-09
forum: Networking &amp; Wireless
---

### Post by lic-mt on 2019-01-09
Hi,

I have a TP LINK T2UHP V1 with the *infamous* MT7610u chipset which is working fine in XP. 
I recently installed Ubuntu 18.04 LTS in an old machine with no 5.8ghz. 

I read that kernel 4.20 has the drivers for this chipset so I upgraded but the adapter is not working.

```
lsusb

Bus 001 Device 004: ID 5986:04a3 Acer, Inc 
Bus 001 Device 006: ID 2357:0123 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


```
sudo -i
modprobe mt76x0u
echo "2357 0123" > /sys/bus/usb/drivers/mt76x0u/new_id
exit

```

```
lsmod | grep mt76x0u

mt76x0u                20480  0
mt76x0_common          73728  1 mt76x0u
mt76x02_usb            16384  1 mt76x0u
mt76_usb               28672  2 mt76x02_usb,mt76x0u
mt76x02_lib            49152  3 mt76x02_usb,mt76x0_common,mt76x0u
mt76                   45056  4 mt76_usb,mt76x02_lib,mt76x0_common,mt76x0u
mac80211              811008  8 mt76,rtl_pci,mt76_usb,mt76x02_lib,rtlwifi,mt76x0_common,rtl8192se,mt76x0u

```

Any ideas?

---

### Post by lic-mt on 2019-02-07
After trying different things the TP LINK T2UHP is working under Kernel 4.20.6


1.
It seems that product ID 0123 of this adapter is not recognized by the driver.
I had the same issue with an old Airlive WL 1600, so I tried the solution here:


[https://ubuntuforums.org/showthread.php?t=1904757&amp;page=5](https://ubuntuforums.org/showthread.php?t=1904757&amp;page=5)


In terminal I edited this file:


```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```


I added this line:


```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="2357", ATTR{idProduct}=="0123", RUN+="/sbin/modprobe -qba mt76x0u"
```


Then I opened this file:


```
sudo gedit /etc/modprobe.d/network_drivers.conf
```


I added the following text:


```
install mt76x0u /sbin/modprobe --ignore-install mt76x0u $CMDLINE_OPTS; /bin/echo "2357 0123" > /sys/bus/usb/drivers/mt76x0u/new_id
```


The adapter was still not working.


2.
After some reading I noted that there was no Mediatek folder in /lib/firmware.


```
sudo dpkg -s linux-firmware | grep Version
Version: 1.173.3
```


I downloaded and installed version 1.175.1 from 
[https://packages.ubuntu.com/search?keywords=linux-firmware](https://packages.ubuntu.com/search?keywords=linux-firmware)




The adapter is working now, both in Ubuntu and Lubuntu.
But there are some issues, like:
-there is no LED flashing,
-sometimes it's hard to connect to a 5.8Gh network. Maybe a Network  Manager thing. I had Wicd in the Lubuntu machine but it was not connecting to 5.8Gh with "bad passsword" error. Reinstalled NM.

5.8Gh speed is ok. Not as fast as in Windows.
And 2.4Gh speed is bad, sometimes a bit more than old dial up connections, 5 to 20Kb/s.

---

