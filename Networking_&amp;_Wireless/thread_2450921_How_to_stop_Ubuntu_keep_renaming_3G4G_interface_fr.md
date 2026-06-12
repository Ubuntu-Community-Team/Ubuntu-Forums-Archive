---
title: "How to stop Ubuntu keep renaming 3G/4G interface from wwan0 to wwx&lt;mac-addr&gt; ?."
date: 2020-09-23
forum: Networking &amp; Wireless
---

### Post by eby on 2020-09-23
Whenever Huawei 3G/4G device is plugged in, it renames to wwx<mac-address> instead of wwan0. How stop renaming and retain wwan0 ?. 

This is a fresh installation of Ubuntu 20.04 LTS.

lsusb
```
Bus 003 Device 004: ID 12d1:1506 Huawei Technologies Co., Ltd. Modem/Networkcard
```

dmesg | grep huawei
```
[  672.819382] huawei_cdc_ncm 3-1:1.0: MAC-Address: <mac-address>
[  672.819387] huawei_cdc_ncm 3-1:1.0: setting tx_max = 16384
[  672.820001] huawei_cdc_ncm 3-1:1.0: NDP will be placed at end of frame for this device.
[  672.820142] huawei_cdc_ncm 3-1:1.0: cdc-wdm0: USB WDM device
[  672.820759] huawei_cdc_ncm 3-1:1.0 wwan0: register 'huawei_cdc_ncm' at usb-0000:45:00.0-1, Huawei CDC NCM device, <mac-address>
[  672.821232] usbcore: registered new interface driver huawei_cdc_ncm
[  672.847974] huawei_cdc_ncm 3-1:1.0 wwx<mac-address>: renamed from wwan0
```


The other requirement is to bring this wwan0 in Network Manager so i can connect/disconnect using GUI, currently invoke dhclient from terminal to get ip from the dongle.

thanks,

---

### Post by praseodym on 2020-09-23
Try
```

sudo apt purge biosdevname
sudo update-initramfs -u
```
Check, if there are no entries in the /etc/network/interfaces with the "new" names anymore, if yes, remove them. Reboot

---

### Post by eby on 2020-09-25
> ~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d

> ~$ sudo apt purge biosdevname
[sudo] password for eby:           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package biosdevname


What next ?.

---

### Post by praseodym on 2020-09-26
Ok, add these kernel parameters to /etc/default/grub

```
net.ifnames=0 biosdevname=0
```
run

```
sudo update-grub
```

and reboot

---

### Post by eby on 2020-10-22
> **praseodym said:**
> Ok, add these kernel parameters to /etc/default/grub

```
net.ifnames=0 biosdevname=0
```
run

```
sudo update-grub
```

and reboot

Thank you verymuch, it worked !!!!.

---

