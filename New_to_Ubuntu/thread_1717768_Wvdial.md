---
title: "Wvdial"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Barankhan on 2011-03-30
I have plugged new device of Green Packet (Media Tek) USB device but i am not able to use it through wvdial 

Green Packet (MediaTek)

lsusb
baran@baran-Inspiron-N5010:~$ lsusb
Bus 002 Device 006: ID 413c:8160 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. 
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. 
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0e8d:7109 MediaTek Inc. 
Bus 001 Device 003: ID 0c45:641d Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

baran@baran-Inspiron-N5010:~$ dmesg
[ 2308.579809] usb 1-1.2: USB disconnect, address 4
[ 2308.674260] scsi 6:0:0:0: rejecting I/O to dead device
[ 2312.616967] usb 1-1.2: new high speed USB device using ehci_hcd and address 5
[ 2312.710328] scsi7 : usb-storage 1-1.2:1.0
[ 2313.709341] scsi 7:0:0:0: CD-ROM            MediaTek WiMAX Install CD 1.00 PQ: 0 ANSI: 0 CCS
[ 2313.711350] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2313.711568] sr 7:0:0:0: Attached scsi CD-ROM sr1
[ 2313.712254] sr 7:0:0:0: Attached scsi generic sg2 type 5
[ 2313.827044] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2313.828169] ISOFS: changing to secondary root


wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.


Please Help me out as i want to use it on UBUNTU.

Thanks,
Baran

---

### Post by khelben1979 on 2011-03-30
If you're attempting to use a USB modem with Ubuntu, I would recommend you less pain with getting yourself an [Ethernet]("http://en.wikipedia.org/wiki/Ethernet") modem instead.

I have read many threads on this forum about problems getting USB modems to work, and if you're looking for an easy solution, go for ethernet instead.

---

### Post by sammiev on 2011-03-30
Please [READ]("http://ubuntuforums.org/showthread.php?t=1589966&page=3") post #22 and my follow up on post #27. GL :)

---

### Post by Barankhan on 2011-03-31
Thanks a lot for your reply. I want to use USB Modem on Ubuntu. I am using development since 2008. I don't want to switch back to windows. Please let me know all the possible solutions. 

I will really be thankful to you.

Regards,
Baran

---

### Post by ntu on 2011-03-31
I cannot recall using Wavedial, sorry, but I did use ppp to get online with Ubuntu 10.4 quite some time ago with an external serial modem. It is at:

```
sudo pppconfig
```

Hope this is of some help.

---

