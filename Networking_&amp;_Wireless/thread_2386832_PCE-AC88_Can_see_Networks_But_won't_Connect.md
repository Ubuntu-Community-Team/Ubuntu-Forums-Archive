---
title: "PCE-AC88 Can see Networks But won't Connect"
date: 2018-03-11
forum: Networking &amp; Wireless
---

### Post by kavidey on 2018-03-11
I just got a used PCE-AC88. It works very well with Windows 10, but I had a lot of trouble with ubuntu. After a few hours of testing and searching, this [https://rhees.nl/2017/03/10/HOWTO-install-drivers-for-the-Asus-PCE-AC88-on-Debian-Jessie/](https://rhees.nl/2017/03/10/HOWTO-install-drivers-for-the-Asus-PCE-AC88-on-Debian-Jessie/) tutorial let my card see networks. If I try and connect to one, ubuntu tries for a few seconds and then just disconnects. I used a completely fresh install of ubuntu 16.04.4.

---

### Post by mörgæs on 2018-03-13
Try to avoid instructions which are built upon backported software. Better to begin with a fresh install of a recent release, that is 17.10.1 or 18.04 (beta).

---

### Post by kavidey on 2018-03-23
I installed Ubuntu 17.10 and ran lshw -C network. Ubuntu could detect that the wireless device was plugged and the manufacturer, but the device was unclaimed. (The other wifi device in the output [IMG]https://drive.google.com/open?id=1Fm4idluAJ9Vb1s07oRlGDpi0rieAisRP[/IMG]is built into my motherboard)[IMG]https://drive.google.com/open?id=1Fm4idluAJ9Vb1s07oRlGDpi0rieAisRP[/IMG]
[https://drive.google.com/open?id=1Fm4idluAJ9Vb1s07oRlGDpi0rieAisRP](https://drive.google.com/open?id=1Fm4idluAJ9Vb1s07oRlGDpi0rieAisRP)

---

### Post by mörgæs on 2018-03-24
Good beginning. 

There are many users here knowing more than me about wifi connections. In order to attract their attention I suggest that you click the report button and ask a moderator to move your post to the networking forum. After that please read the sticky notes in that forum and follow the instructions.

---

### Post by wildmanne39 on 2018-03-24
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

---

### Post by praseodym on 2018-03-25
Please run the wireless script from the sticky thread and show the outputs

---

### Post by kavidey on 2018-04-01
I ran the wireless script[ http://paste.ubuntu.com/p/xbkjmCGJ67/]("http://paste.ubuntu.com/p/xbkjmCGJ67/") was the result.

---

### Post by jeremy31 on 2018-04-01
Your realtek internal should work after
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```
Reboot

Make sure Secure Boot is disabled

---

### Post by kavidey on 2018-04-01
Thank you for that fix. The only issue is that the realtek internal is much slower that the broadcom device. Is there any way to get the broadcom device working too?

---

### Post by jeremy31 on 2018-04-01
Try ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot and see if the broadcom works

---

### Post by kavidey on 2018-04-01
I tried that and I don't think it worked. I ran "lshw -C network" and the broadcom device was still unclaimed. I also ran the network script and the result is here: [http://paste.ubuntu.com/p/5P7SP7vJZQ/](http://paste.ubuntu.com/p/5P7SP7vJZQ/)

---

### Post by jeremy31 on 2018-04-02
What happens when you ```
sudo modprobe -v brcmfmac
```

---

### Post by praseodym on 2018-04-02
Plus (again)
```

dmesg | egrep 'brcm|firm|fail'
```

---

### Post by kavidey on 2018-04-02
[FONT=Courier New]sudo modprobe -v brcmfmac[/FONT] Outputs nothing and [FONT=Courier New]dmesg | egrep 'brcm|firm|fail'[/FONT] Outputs 

```
[    0.096966] ACPI Error: [_SB_.PCI0.RP05.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170531/dswload2-191)
[    0.096972] ACPI Error: Method parse/execution failed \_SB.PCI0.RP04.PXSX, AE_NOT_FOUND (20170531/psparse-550)
[    0.097180] ACPI Error: [_SB_.PCI0.RP09.PXSX] Namespace lookup failure, AE_NOT_FOUND (20170531/dswload2-191)
[    0.097184] ACPI Error: Method parse/execution failed \_SB.PCI0.RP08.PXSX, AE_NOT_FOUND (20170531/psparse-550)
[   10.045580] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   10.277843] rtl8822be: Using firmware rtlwifi/rtl8822befw.bin
[   10.530794] usbcore: registered new interface driver brcmfmac
[   10.530803] brcmfmac 0000:02:00.0: enabling device (0000 -> 0002)
[   10.654791] brcmfmac 0000:02:00.0: Direct firmware load for brcm/brcmfmac4366c-pcie.bin failed with error -2

```

---

### Post by jeremy31 on 2018-04-02
Try this```
cd /lib/firmware/brcm
sudo wget https://blog.cooperteam.net/brcmfmac4366c-pcie.bin
```
Reboot

---

### Post by kavidey on 2018-04-02
Downloading that driver worked! Is this a permanent fix, or would I need to re-download the driver every time I update?

---

### Post by jeremy31 on 2018-04-02
It should be permanent

---

### Post by praseodym on 2018-04-06
I contacted the maintainers of "linux-firmware" to add it for Bionic

---

### Post by praseodym on 2019-02-17
Firmware available in "linux-firmware" of 19.04:

```
wget http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.177_all.deb
sudo dpkg -i linux-firmware_1.177_all.deb
```
Worked ootb in the German forum

---

