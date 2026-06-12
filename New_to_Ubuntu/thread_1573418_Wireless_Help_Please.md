---
title: "Wireless Help Please"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Taylorrice16 on 2010-09-12
I am having a lot of trouble getting my wireless to work. I recently installed ubuntu 10.04 lucid, I have a wpa encryption. My wireless card sees the network however does not connect to it. Please help if you can!

---

### Post by Miljet on 2010-09-12
Welcome to Ubuntu and these forums. We need much more information to be able to help. 

Have you tried clicking on the network and entering your wpa passcode?

Can you temporarily connect with an ethernet cable? If so, go to System -> Administration -> Hardware drivers. It will search for drivers for your wireless card and offer to install them if any are found.

What is the computer make and model?

Which wireless card does it use? Open a terminal by clicking on Applications -> Accessories -> Terminal and either type in the following, or copy and paste it in the terminal. Then copy and paste the output here and we can determine the wireless card.

---

### Post by bkratz on 2010-09-12
> **Taylorrice16 said:**
> I am having a lot of trouble getting my wireless to work. I recently installed ubuntu 10.04 lucid, I have a wpa encryption. My wireless card sees the network however does not connect to it. Please help if you can!



Well if you see the networks you obviously have the driver installed and could connect unencrypted. I have seen a few posts that complain about being unable to connect to WPA networks when the router is set to mixed WPA and WPA2 mode. Please check your router and, if it is set so, change it to WPA2 only, assuming all the devices on your network do WPA2. I also had to set mine to AES only not TKIP/AES.

---

### Post by Taylorrice16 on 2010-09-12
I entered the passcode, yes, but It wont connect it tries but it just times out...

I think I have broken it further by trying to fix it myself because now I cannot even see the wireless networks anymore.

when I attempt to find drivers it only brings up ones for my graphics card, not my wireless card.

it is a gateway fx laptop model #  P-6860fx

Here is my lspci :

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800M GTS] (rev a2)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:06.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)


Idk what you can make of that but anything helps thank you!

---

### Post by Taylorrice16 on 2010-09-13
I have been told that intel/realtek should work out of the box, im thinking its my encryption settings on my router.... Is there a suggested encryption for ubuntu, one that works well?

---

