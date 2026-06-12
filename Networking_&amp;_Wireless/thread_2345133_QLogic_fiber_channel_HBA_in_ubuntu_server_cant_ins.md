---
title: "QLogic fiber channel HBA in ubuntu server cant install drivers please help"
date: 2016-11-30
forum: Networking &amp; Wireless
---

### Post by lkes on 2016-11-30
Hi,

I have recently aquired a Ds14 mk4 fiber channel storage array and some qlogic 2462 duel port 4gbps pcie hba's. after watching a hotnoob video on youtube and verifying it myself i have decided i need to use linux to format the drives to a format that windows server can read, as in my testing windows server 2016 can detect all of the drives but on mark them online or do anything with them. I have installed sg3_utils for formatting the drives and my only issue is how do i install the drivers? qlogic only supports redhat and sues linux and i tried installing those drivers on ubuntu desktop with some luck. it went through the installer but errored out saying could not find rpm file. I am lost as far as trying to run it again on ubuntu server as i have been windows all my life. 
any help would be greatly appreciated
thanks

---

### Post by chili555 on 2016-11-30
> qlogic 2462 duel port 4gbps pcieWow! My favorite kind of problem! I know *nothing* about the subject but I'll learn along with you.

Looking at the driver package from Qlogic suggests that these devices use the driver *qla2xxx* that is already included in recent Ubuntu versions. Confirm the device from the terminal:```
lspci -nnk
```See if the driver is already included:```
modinfo qla2xxx
```Did the driver load?```
lsmod | grep qla
```Does the log suggest that firmware is needed?```
dmesg | grep qla
```


----------------
Reference:```
$ modinfo qla2xxx 
filename:       /lib/modules/4.8.0-27-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
firmware:       ql2500_fw.bin
firmware:       ql2400_fw.bin
firmware:       ql2322_fw.bin
firmware:       ql2300_fw.bin
firmware:       ql2200_fw.bin
firmware:       ql2100_fw.bin
version:        8.07.00.38-k
license:        GPL
description:    QLogic Fibre Channel HBA Driver
author:         QLogic Corporation

```

---

### Post by lkes on 2016-12-01
thanks for the tips, i will try it out in half an hour and let you know how it goes

---

### Post by lkes on 2016-12-01
[ATTACH=CONFIG]272494[/ATTACH][ATTACH=CONFIG]272495[/ATTACH][ATTACH=CONFIG]272496[/ATTACH][ATTACH=CONFIG]272497[/ATTACH][ATTACH=CONFIG]272498[/ATTACH]alright i think i have narrowed down the issue to two things, one of which i have fixed.

the first one and something i should have checked was if the hba card was even good as i had just gotten it off of ebay used. i swapped it for a known good one i had in my windows server that detected all of the drives no problem. i put it in the ubuntu server and boom IT WORKED............but didnt do what i wanted. It did get a link up on both ports of the cards as the leds on the back of the card said the 1gbps or the 4gbps whichever i set my storage server to. also when i ran (what i believe is [COLOR=#000000][FONT=&amp]dmesg | grep qla) it said it found a linkup and down of 1gbps which is all and good except when i tried to do what i have been wanting to do.... use sg3_utils to format the drives to something windows can read. i ran the sginfo -l to list the drives and none were found:( which is weird as windows found all of them once i realized my fiber cable was bad the first time lol. i went back to the hotnoob video i had watched and a viewer commented that he had to [/FONT][/COLOR][COLOR=#000000][FONT=Roboto]enable the QLogic HBA BIOS. Which apparently is disabled by default.&#65279; i replied to his comment and am waiting on a responce and have googled the subject with no help whatsoever. 

I attached some pictures of the screen during different commands[/FONT][/COLOR]

---

