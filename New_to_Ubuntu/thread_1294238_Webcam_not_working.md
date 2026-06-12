---
title: "Webcam not working"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Konbuntu on 2009-10-18
I'm trying to use my microsoft lifecam nx-6000 webcam with ubuntu 8.04 but for some reason i can't get it to work. i tried it using with amsn and it didn't work, it didn't recognize it.. maybe i need to update something.. i don't know =/

---

### Post by rajeev1204 on 2009-10-18
> **Konbuntu said:**
> I'm trying to use my microsoft lifecam nx-6000 webcam with ubuntu 8.04 but for some reason i can't get it to work. i tried it using with amsn and it didn't work, it didn't recognize it.. maybe i need to update something.. i don't know =/

Can you post the output of lspci from a terminal.

Also test the webcam with cheese.

```
sudo apt-get install cheese
```

Also do```
update pciids
```

---

### Post by lrcaballero on 2009-10-18
You need to install Cheese, here is the link to a previous thread!!

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

Luis

---

### Post by lrcaballero on 2009-10-18
Also try this: 

sudo modprobe uvcvideo

sudo apt-get install cheese

cheese

Luis

---

### Post by Konbuntu on 2009-10-18
> **rajeev1204 said:**
> Can you post the output of lspci from a terminal.




kon@kon-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by Konbuntu on 2009-10-18
one more thing, every time i try to turn my webcam on with amsn the program crashes!

thanks for you guys' help!

---

### Post by rajeev1204 on 2009-10-18
Sorry

Output of lsusb from a terminal.Its a usb webcam right?

---

### Post by Konbuntu on 2009-10-18
that's right!

---

### Post by rajeev1204 on 2009-10-18
> **Konbuntu said:**
> that's right!


Please post the output of lsusb from a terminal.

Also try this link [http://ubuntuforums.org/showpost.php?p=5826879&postcount=4](http://ubuntuforums.org/showpost.php?p=5826879&postcount=4)

---

