---
title: "mmcli does not find modem Huawei E3272 on ubuntu 16.04."
date: 2017-05-10
forum: Networking &amp; Wireless
---

### Post by dk1979 on 2017-05-10
Hi all, I have installed an ubuntu VM 16.04 on a windows 7 host. [COLOR=#111111][FONT=Ubuntu]I connected the 4g modem. The ifconfig gives the following additional interface:
[/FONT][/COLOR]enx0c5b8f279a64 Link encap:Ethernet  HWaddr 0c:5b:8f:27:9a:64 

[COLOR=#111111][FONT=Ubuntu]which works fine and have internet access via 4g network. Apart from that I need to get additional cellular data from modem like MNC,MCC, signal strength etc, but don't want to get from the relevant web api. So I tried to get them via ModemManager mmcli but I got the following printout when giving "mmcli -L":

[/FONT][/COLOR]```
No modems were found 
```

I disconnected the usb dongle and recconnected after 5 seconds and get the following printouts:

Output of command lsusb:

```
Bus 001 Device 004: ID 12d1:14dc Huawei Technologies Co., Ltd. 
```

Output of command dmesg|tail:

```
[ 2990.932837] usb 1-2: Product: HUAWEI_MOBILE
[ 2990.932838] usb 1-2: Manufacturer: HUAWEI_MOBILE
[ 2991.139073] rndis_host 1-2:1.0 eth0: register 'rndis_host' at usb-0000:00:0c.0-2, RNDIS device, 0c:5b:8f:27:9a:64
[ 2991.140976] usb-storage 1-2:1.2: USB Mass Storage device detected
[ 2991.141154] scsi host4: usb-storage 1-2:1.2
[ 2991.225766] rndis_host 1-2:1.0 enx0c5b8f279a64: renamed from eth0
[ 2991.266112] IPv6: ADDRCONF(NETDEV_UP): enx0c5b8f279a64: link is not ready
[ 2992.147124] scsi 4:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 2992.150263] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2992.156126] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```
Output of command cat -n /etc/fstab:
```

     1    # /etc/fstab: static file system information.
     2    #
     3    # Use 'blkid' to print the universally unique identifier for a
     4    # device; this may be used with UUID= as a more robust way to name devices
     5    # that works even if disks are added and removed. See fstab(5).
     6    #
     7    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
     8    # / was on /dev/sda1 during installation
     9    UUID=f2bb050d-969d-489e-a5db-cf6a1cc770c4 /               ext4    errors=remount-ro 0       1
    10    # swap was on /dev/sda5 during installation
    11    UUID=54fa6b7d-0a1d-4ee2-9944-db918c9c9c75 none            swap    sw              0       0

```


Output of command ls -l /dev/ttyu* /dev/ttyU*:

```
ls: cannot access '/dev/ttyu*': No such file or directory
ls: cannot access '/dev/ttyU*': No such file or directory
```

Output of command sudo usb_modeswitch -v 12d1 -p 14dc -J -R -W:

```
Take all parameters from the command line




* usb_modeswitch: handle USB devices with multiple modes
* Version 2.2.5 (C) Josua Dietze 2015
* Based on libusb1/libusbx


! PLEASE REPORT NEW CONFIGURATIONS !


DefaultVendor=  0x12d1
DefaultProduct= 0x14dc
HuaweiNewMode=1
NeedResponse=0


Look for default devices ...
found USB ID 1d6b:0003
found USB ID 12d1:14dc
vendor ID matched
product ID matched
found USB ID 80ee:0021
found USB ID 1d6b:0002
Found devices in default mode (1)
Access device 003 on bus 001
Current configuration number is 1
Use interface number 0
Error: message endpoint not given or found. Abort
```


I also find on google that most probably the modem mode is[COLOR=#333333][FONT=Ubuntu] 12d1:1506 but 

[/FONT][/COLOR]Output of command sudo usb_modeswitch -v 12d1 -p 1506 -J -R -W:[COLOR=#333333][FONT=Ubuntu]

[/FONT][/COLOR]```
Take all parameters from the command line




 * usb_modeswitch: handle USB devices with multiple modes
 * Version 2.2.5 (C) Josua Dietze 2015
 * Based on libusb1/libusbx


 ! PLEASE REPORT NEW CONFIGURATIONS !


DefaultVendor=  0x12d1
DefaultProduct= 0x1506
HuaweiNewMode=1
NeedResponse=0


Look for default devices ...
  found USB ID 1d6b:0003
  found USB ID 12d1:14dc
   vendor ID matched
  found USB ID 80ee:0021
  found USB ID 1d6b:0002
 No devices in default mode found. Nothing to do. Bye!
```

Has anyone has any idea what I'm doing wrong here?

---

