---
title: "How do I install firmware-b43-installer without internet?"
date: 2015-11-22
forum: Networking &amp; Wireless
---

### Post by ardouronerous on 2015-11-22
I'm planning on installing Xubuntu 14.04 on my father's laptop, which is a Dell Inspiron E1505, and it uses Dell Wireless 1390 WLAN Mini-Card, and I found that in order to use Dell Wireless 1390 WLAN Mini-Card, I need to install firmware-b43-installer.

Do I actually need internet connection to install Xubuntu, as suggested by the installer? If so, the problem is, I cannot connect directly to the internet due to distance problems, the main internet modem is located on the 2nd floor of the house, my father's room is on the 1st floor, and it is a hassle to carry the laptop to the 2nd floor, so I'm trying to find ways to install firmware-b43-installer without internet.

In my experience, using the Broadcom STA wireless driver from Additional Drivers, is bad, it's buggy and it even stops my computer from shutting down properly.

While googling the problem, I found this:

'firmware-b43-installer_018-2_all.deb' from [http://packages.ubuntu.com/trusty/kernel/firmware-b43-installer](http://packages.ubuntu.com/trusty/kernel/firmware-b43-installer)

Can I download this, put it on a USB, transfer it to my father's laptop during the live CD session, and install this to access my house's wifi and then install Xubuntu with the required internet connection?

---

### Post by jeremy31 on 2015-11-22
Try selecting a download site from [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download) and install it and try ```
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe ssb
sudo modprobe b43
```
It might hang in terminal with the last command but you can't reboot and keep the firmware from live version.  It worked for people just over a year ago

---

### Post by Hadaka on 2015-11-22
@jeremy31, linux-firmware-nonfree is no longer valid.
please try this method.
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717) 
*post #7
be sure to drag and drop the zip file first to your desktop
then issue the commands.
thanks.

---

### Post by jeremy31 on 2015-11-22
> **Hadaka said:**
> @jeremy31, linux-firmware-nonfree is no longer valid.
please try this method.
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717) 
*post #7
be sure to drag and drop the zip file first to your desktop
then issue the commands.
thanks.

Strange, it shows the b43 firmware in the file list but they aren't in the download.  I knew they changed it in the trusty repos over a year ago

---

### Post by praseodym on 2015-11-22
Download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation

```
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by chili555 on 2015-11-22
> **praseodym said:**
> Download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation

```
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
RebootI believe the firmware goes in its own directory b43. Therefor, I suggest:```
sudo mkdir /lib/firmware/b43
sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/b43
```Reference:```
chili@ThinkT60:~$ modinfo b43
filename:       /lib/modules/4.2.0-040200rc3-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       [COLOR="#FF0000"]b43[/COLOR]/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
<snip>
```

---

### Post by ardouronerous on 2015-11-23
@praseodym and @chili555, unfortunately your method requires that I reboot, but in a live CD environment, I cannot reboot, and according to Xubuntu installer, I need to be connected to the internet in order to install Xubuntu, but do I actually need internet connection to install Xubuntu, as suggested by the installer?

@Hadaka, does your method require rebooting?

---

### Post by Hadaka on 2015-11-23
Hi,you can probably pull it off without booting,however as you know
the first time you boot,its gone.These broadcom wireless drivers are
tried and true, and there is basically only 2 types used..the b43 and the broadcom-kernel-source.
just to verify that you do need the b43 please copy and paste..
```
lspci -n | awk '/0280/{print$3}'
```
post the output
thanks.

---

### Post by ardouronerous on 2015-11-23
Unfortunately, the 10-year-old hard drive of the laptop finally failed, so I'm now in the process of searching for a new hard drive before I install Xubuntu.

I will post the output if and when the laptop is repaired and is in working order.

Thanks for the help!:D

---

### Post by praseodym on 2015-11-24
Even in a live system you only need to reload the driver after installing the firmware:
```

sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

