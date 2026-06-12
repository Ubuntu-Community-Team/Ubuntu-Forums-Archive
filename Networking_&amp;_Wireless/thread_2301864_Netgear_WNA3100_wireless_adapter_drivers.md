---
title: "Netgear WNA3100 wireless adapter drivers?"
date: 2015-11-05
forum: Networking &amp; Wireless
---

### Post by Sean_Vigent on 2015-11-05
Hi, I have a Dell Optiplex 760 and the only way I connect to the internet is with a Netgear WNA3100 Wireless adapter. I have installed Ubuntu on my system and like I expected, I wasn't able to connect to the internet. I do not have any other internet connection on this computer, but I can install things using Windows 7 (It's dual booted).

I know there are several posts about this, but they are all if you are able to get internet connection. I don't have any internet connection and I'm not able to get internet connection, so the only way I can install things is through a USB or dual booting Windows 7.

When I type in lsusb, this is the adapter:
Bus 002 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

---

### Post by kurt18947 on 2015-11-06
Have you searched in the networking and wireless area? If not, I'd recommend doing so. I don't have that adapter so haven't kept up with any progress made in installing it. The last I knew you have to use NDISwrapper and WinXP drivers, 32 or 64 bit as appropriate. If practical, buying a device known to be plug 'n' play is SO much simpler.

---

### Post by Sean_Vigent on 2015-11-06
What do you mean by "Networking and Wireless" area? If you mean on the forums then yes.

---

### Post by jeremy31 on 2015-11-06
Find a TP-Link WN-722N USB wifi adapter, it is plug in and play in Ubuntu and the external antenna gets good reception

---

### Post by Sean_Vigent on 2015-11-06
I currently can't right now and I would like to use my current.

---

### Post by tokyobadger on 2015-11-07
The solution is in [this thread]("http://ubuntuforums.org/showthread.php?t=2221251")

1. Download the required Ubuntu packages from [here]("http://packages.ubuntu.com/") when in Windows 7, transfer to a USB stick or other media that you can access from Ubuntu

2. Download the driver from [here]("http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz") and transfer to other media as in #1 above

3. Boot Ubuntu, transfer the Ubuntu files (.deb files) to your /home/Downloads and install with sudo dpkg -i

4. Unpack the driver in /home/Downloads and install (attention to 32-bit or 64-bit) - note that the driver version is for v2 and you have v1 but the device ID is identical - if it doesn't work, find the driver for v1
**edit: just saw that the OP in the linked "SOLVED" thread also had v1 but appears to have fixed with the v2 driver**

5. Load the driver and configure

That thread was active until August of 2015 - as suggested, you'd probably get better suggestions in the Networking & Wireless area of the forums

---

### Post by Sean_Vigent on 2015-11-07
Sorry, I'm fairly new to Ubuntu. What "Required packages" do I need to install?

Also, when I wrote this I didn't know there was a Networking & Wireless forum. Oops.

---

### Post by tokyobadger on 2015-11-07
From post #4 of the linked thread: 
ndisgtk ndiswrapper-dkms dkms linux-headers-generic build-essential

Post #17 shows how to install those packages; Post #8 has the steps for installing the driver

And to be honest I think you'd be better off posting in that thread so as to keep related issues and solutions consolidated in one place

---

### Post by Bucky Ball on 2015-11-07
> **Sean_Vigent said:**
> What do you mean by "Networking and Wireless" area? 

*Thread moved to **Networking and Wireless**.*

This belongs here. :)

---

