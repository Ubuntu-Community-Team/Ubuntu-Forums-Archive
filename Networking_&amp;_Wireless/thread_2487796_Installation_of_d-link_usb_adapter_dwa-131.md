---
title: "Installation of d-link usb adapter dwa-131"
date: 2023-06-15
forum: Networking &amp; Wireless
---

### Post by AnupamMitra on 2023-06-15
My Desktop is UBUNTU 22.04 64 BIT.

I found that the  D-Link Wireless N Nano USB Adapter doesn't get detected and installed  automatically. 

  Following are the adapter specifications:

  
[LIST]
[*]Model No: DWA-131
[*]Hardware Version : E1
[*]Firmware Version : 5.12
[/LIST]
  How to install this wireless adapter in my PC?

---

### Post by jeremy31 on 2023-06-16
Post results from terminal for ```
lsusb
```

---

### Post by AnupamMitra on 2023-06-17
> **jeremy31 said:**
> Post results from terminal for ```
lsusb
```

Sorry for the delay in sending the required information. The result is as under:
```

anupam@anupam-ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04d9:1203 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 005: ID 2001:3319 D-Link Corp. DWA-131 Wireless N Nano Adapter (Rev. E1) [Realtek RTL8192EU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
anupam@anupam-ubuntu:~$ 

```

---

### Post by jeremy31 on 2023-06-17
Post result from terminal for ```
sudo dmesg | egrep -i 'rtl8xxxu|3319'
```

---

### Post by AnupamMitra on 2023-06-17
> **jeremy31 said:**
> Post result from terminal for ```
sudo dmesg | egrep -i 'rtl8xxxu|3319'
```

The result is as under.
```

anupam@anupam-ubuntu:~$ sudo dmesg | egrep -i 'rtl8xxxu|3319'
[sudo] password for anupam: 
[    0.133199] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    1.833190] usb 1-5: new low-speed USB device number 4 using xhci_hcd
[  379.050559] usb 1-3: New USB device found, idVendor=2001, idProduct=3319, bcdDevice= 2.00
[  379.185702] usb 1-3: This Realtek USB WiFi dongle (0x2001:0x3319) is untested!
[  379.249725] usb 1-3: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[  380.163134] usbcore: registered new interface driver rtl8xxxu
[  380.182127] rtl8xxxu 1-3:1.0 wlxa42a95459718: renamed from wlan0
[ 4435.331983] mt7601u 1-3:1.0: Warning: mt7601u_mcu_wait_resp retrying
[ 5093.051295] usb 1-3: New USB device found, idVendor=2001, idProduct=3319, bcdDevice= 2.00
[ 5093.057779] usb 1-3: This Realtek USB WiFi dongle (0x2001:0x3319) is untested!
[ 5093.122942] usb 1-3: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[ 5094.097669] rtl8xxxu 1-3:1.0 wlxa42a95459718: renamed from wlan0
anupam@anupam-ubuntu:~$ 

```

---

### Post by jeremy31 on 2023-06-17
You could try another driver but check ```
mokutil --sb
``` as Secure Boot will need to be disabled
```
sudo apt install git dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot

---

### Post by AnupamMitra on 2023-06-18
> **jeremy31 said:**
> You could try another driver but check ```
mokutil --sb
``` as Secure Boot will need to be disabled
```
sudo apt install git dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot

Thanks for your support.  I applied all the commands, as suggested, and after rebooting I inserted the adapter in the port but unfortunately it is yet to be detected and/or installed by/in the PC.  

Awaiting for your further advice.

---

### Post by jeremy31 on 2023-06-18
See the wireless script link in my signature and post results

---

### Post by AnupamMitra on 2023-06-18
> **jeremy31 said:**
> See the wireless script link in my signature and post results

```

anupam@anupam-ubuntu:~$ sudo apt update
[sudo] password for anupam: 
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease                         
Get:2 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease [7,553 B]
Hit:3 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                 
Get:4 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease [7,459 B]
Hit:5 https://ppa.launchpadcontent.net/audio-recorder/ppa/ubuntu jammy InRelease
Hit:6 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:7 http://archive.ubuntu.com/ubuntu jammy-backports InRelease               
Get:8 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7,452 B]
Hit:9 http://archive.ubuntu.com/ubuntu jammy-security InRelease                
Ign:10 https://ppa.launchpadcontent.net/mordec13/youtubedl-gui/ubuntu jammy InRelease
Err:11 https://ppa.launchpadcontent.net/mordec13/youtubedl-gui/ubuntu jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done                                                  
E: The repository 'https://ppa.launchpadcontent.net/mordec13/youtubedl-gui/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
anupam@anupam-ubuntu:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-remote-desktop grub-common grub-pc grub-pc-bin grub2-common
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
anupam@anupam-ubuntu:~$ sudo apt install pastebinit
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
pastebinit is already the newest version (1.5.1-1ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
anupam@anupam-ubuntu:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
--2023-06-18 23:27:48--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 20.207.73.82
Connecting to github.com (github.com)|20.207.73.82|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2023-06-18 23:27:49--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.108.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17534 (17K) [text/plain]
Saving to: 'wireless-info'

wireless-info       100%[===================>]  17.12K  --.-KB/s    in 0.001s  

Last-modified header missing -- time-stamps turned off.
2023-06-18 23:27:49 (15.2 MB/s) - 'wireless-info' saved [17534/17534]


Results saved in "/home/anupam/wireless-info.txt".

Results also archived in "/home/anupam/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

anupam@anupam-ubuntu:~$    

```

---

### Post by jeremy31 on 2023-06-18
Try enabling wifi and reboot.  The results show a soft block on wifi and it looks like it was likely done in settings somewhere

---

### Post by AnupamMitra on 2023-06-19
> **jeremy31 said:**
> Try enabling wifi and reboot.  The results show a soft block on wifi and it looks like it was likely done in settings somewhere

Thanks a lot. On your advice, today morning I simply went for reboot after inserting the adapter and matter got resolved.  Thanks for your continuous support.

---

