---
title: "Request - Add Realtek RTL8852BE driver to Kernel?"
date: 2023-03-06
forum: Networking &amp; Wireless
---

### Post by landrover74656 on 2023-03-06
Is there a way to submit a formal request to have a driver added to the Linux Kernel?  

I and many others have Realtek RTL8852BE Wifi 6 cards which do not currently have a driver supported in the kernel.  Though the driver can be downloaded and installed manually (using the instructions below) every time there's a software update pushed I have to delete the old driver, connect to a docking station with an RJ45 connection and reinstall the WIFI driver...  

sudo apt update
sudo apt install git bc
git clone [https://github.com/HRex39/rtl8852be.git](https://github.com/HRex39/rtl8852be.git)
cd rtl8852be
make
sudo make install
sudo modprobe 8852be

inxi -Fxpmrz && lsusb && lspci && rfkill list all && mokutil --sb-state

Thanks in advance for your consideration.

---

### Post by chili555 on 2023-03-07
First of all, I suspect that this is a better source for the driver: [https://github.com/lwfinger/rtw89](https://github.com/lwfinger/rtw89)

> I have to delete the old driver, connect to a docking station with an RJ45 connection and reinstall the WIFI driver...I doubt that is necessary. I suggest, after a kernel update and the requested reboot:

```
cd rtl8852be
make clean
make
sudo make install
sudo modprobe 8852be
```In other words, if the kernel update is simply from 5.15.0-x to 5.15.0-y, then it is very unlikely to require an entirely fresh git clone for the wireless to work. After the wireless is working, you can always do:

```
cd rtl8852be
make clean
git pull 
make
sudo make install
sudo modprobe -r 8852be 
sudo modprobe 8852be
```*git pull *refreshes the driver fiie with any changes, improvements, etc.

There are no Ubuntu developers here that I've ever heard from or about. We're all unrelated volunteers, so this probably isn't a place for a feature request. You are encouraged to add to the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002601](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002601)

---

### Post by landrover74656 on 2023-03-07
> **chili555 said:**
> First of all, I suspect that this is a better source for the driver: [https://github.com/lwfinger/rtw89](https://github.com/lwfinger/rtw89)

I doubt that is necessary. I suggest, after a kernel update and the requested reboot:

```
cd rtl8852be
make clean
make
sudo make install
sudo modprobe 8852be
```In other words, if the kernel update is simply from 5.15.0-x to 5.15.0-y, then it is very unlikely to require an entirely fresh git clone for the wireless to work. After the wireless is working, you can always do:

```
cd rtl8852be
make clean
git pull 
make
sudo make install
sudo modprobe -r 8852be 
sudo modprobe 8852be
```*git pull *refreshes the driver fiie with any changes, improvements, etc.

There are no Ubuntu developers here that I've ever heard from or about. We're all unrelated volunteers, so this probably isn't a place for a feature request. You are encouraged to add to the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002601](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002601)


Thank you so much for the prompt response, and suggestions to port the drivers over from one kernel update to another.  That's super helpful.  I've been using Linux as a secondary operating system for 10 years and never had compatibility issues until I got this current machine.

I get that the developers aren't monitoring the forums, but I spent quite a bit of time trying to figure out how one would even submit a request for a driver to be added to the kernel.  I'll try adding to the bug report.

---

### Post by morrownr on 2023-03-22
> I and many others have Realtek RTL8852BE Wifi 6 cards which do not currently have a driver supported in the kernel.

This doesn't sound right. I monitor the linux-wireless list where patches are posted and information is exchanged and I see regular patches for the rtl8852. The 8852be driver is in the RTW89 folder. I can see it in Linus' kernel which is at 6.3.-rc3 right now. Maybe this driver was not activated until a kernel later than what you have or the driver does not include the device ID of your specific card. I think you are trying to ask for something that is already there.

I mostly just pay attention to usb wifi but I think you may need to look closer. Maybe you could install the HWE kernel which I think is at 5.19 to see what happens. Heck, I have a checklist that would help you upgrade all the way to 6.3.rc3 if you want to check that out.

---

### Post by SeijiSensei on 2023-03-22
What happens if you run "sudo ubuntu-drivers"? Does it see the card and suggest a driver?

---

### Post by morrownr on 2023-03-23
Did a upgrade on a Ubuntu 22.04 based system today:

linux-firmware

Wireless: Enable RTL8852BE wifi driver (LP: #2002601)
    - rtw89: 8852b: update fw to v0.27.32.1

---

### Post by bimblesticks on 2023-04-21
Old thread I know but I thought I should mention for anyone that stumbles across here that if you're running Jammy Jellyfish you can use the 6.1 OEM kernel instead of having to compile a driver from GitHub. It's maintained and supported by Canonical and contains backported support for the adapter (see here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002601](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002601)).

Run `sudo apt install linux-oem-22.04c`

Support will be available on the Jammy HWE kernel some time in August, once the kernel from Lunar Lobster is backported.

---

### Post by chili555 on 2023-04-21
The driver is included by default in Ubuntu 23.04:```
/usr/lib/modules/6.2.0-20-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw89_8852be.ko
```

---

### Post by prmbasheer on 2024-01-09
> **chili555 said:**
> The driver is included by default in Ubuntu 23.04:```
/usr/lib/modules/6.2.0-20-generic/kernel/drivers/net/wireless/realtek/rtw89/rtw89_8852be.ko
```

Thanks so much!! I wouldn't have known but for this post. 
I bought a new budget laptop for casual use during the holiday season and it reached me today. I tried LinuxMint and Debian 12. Both of them couldn't spot the Realtek RT8852BE. 
Installed Ubuntu 23.10 and had no issues identifying the Wi-Fi device. Other things seem to be working fine too. Yet to test fully. Once done, will wipe SSD and full install Ubuntu 23.10.
Thanks!!! [COLOR=#000000]chili555

Update: Testing completed. Everything that I need is working as it should be. Installed Ubuntu 23.10 on the full SSD wiping the default Windows 11 it came with. I have got nothing against Windows 11. Regular WIndows user. This budget laptop cannot survive WIndows 11!.
[/COLOR]

---

