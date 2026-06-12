---
title: "Samsung Galaxy Book SM-W620 - WiFi assistance - Qualcomm Atheros QCA6174"
date: 2018-01-28
forum: Networking &amp; Wireless
---

### Post by makem2 on 2018-01-28
I have just purchased the above machine from John Lewis as £349 which seems a great price for the spec. I can return the machine within 35 days if not satisfied.

I want to run xubuntu but need assistance in where to start with enabling networking. The machine only has one 'C' USB port and I am trying xubuntu so taking up that port.

For networking I see:

WiFi Networks
Device not ready
Enable networking - checked
Enable WiFi - checked

The networking icon is greyed out.

As I intend to return the machine for a refund if I cannot get most of the available facilities working, I do not want to move Windows 10 which is currently installed, to install xubuntu. I also do not want to buy a 1 to 2 'C' USB port adaptor if it can be avoided.

I have obtained some information about the networking device using Bluetooth:

```
xubuntu@xubuntu:~$ [COLOR=#000000][FONT=&amp]lspci -nnk | grep 0280 -A2
[/FONT][/COLOR]&#8203;01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)    Subsystem: Samsung Electronics Co Ltd QCA6174 802.11ac Wireless Network Adapter [144d:c150]
    Kernel driver in use: ath10k_pci
xubuntu@xubuntu:~$
```

Is there a driver for this device available for download? If not, without using a WiFi dongle (I do have one), could I build a driver (with help :) )?

I have some experience of building a WiFi driver for another Chinese machine with help from the forum member chilli555.

Searching produces many posts in respect of this device and I am wary of messing things up if I have to return the machine. I also need to download files from git which I cannot see a way to do.

---

### Post by praseodym on 2018-01-28
Driver is already there (ath10k_pci) you may want to update the firmware
```

sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

### Post by makem2 on 2018-01-28
I don't have access to networking/internet, except from windows 10, or from another linux machine.

Also, I am 'trying' xubuntu. It is not installed

---

### Post by praseodym on 2018-01-28
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.169.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.169.1_all.deb)

So download this one and install it via double click. Reboot then

---

### Post by makem2 on 2018-01-28
> **praseodym said:**
> [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.169.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.169.1_all.deb)

So download this one and install it via double click. Reboot then

Thanks. I've been trying linux-firmware_1.157.16_all.deb which I thought was the latest. Got errors about parsing when I tried to install. Trying your suggestion but it takes ages to transfer the file via bluetooth.

---

### Post by makem2 on 2018-01-28
Tried your suggestion but the install hung. Tried installing from terminal but the install is disabled because in read-only mode.

I cannot install a WiFi driver unless I first install the operating system. Correct?

Thats a pain in my case but it appears unavoidable to check that I can in fact get a WiFi driver installed and download the latest software.

Seems a failing in Linux if you can't test the OS fully?

---

### Post by makem2 on 2018-01-28
Please take a rest from this request for assistance.

I have just found that if I choose to install xubuntu alongside windows 10 the maximum space allowed to shrink the windows partition is 4.45GB!

That is even after using the Compact.exe facility which is supposed to reduce the size of windows. A 64GB eMMC is consumed by windows.

I suppose I could install xubuntu on a 256GB SD card or better still move windows there!

---

