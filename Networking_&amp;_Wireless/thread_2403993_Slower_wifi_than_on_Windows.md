---
title: "Slower wifi than on Windows"
date: 2018-10-18
forum: Networking &amp; Wireless
---

### Post by ryuushen on 2018-10-18
Hello, 
I'm completely new to Ubuntu, literally just installed it this morning moving fro Windows 10
I installed it on Acer Predator Helios 300, intel NVME M.2 
So after reading threads about slow wifi on Ubuntu, i tried to **iwlwifi** config and stuff and also checked this: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) to get the right driver
However mine still not getting over 100 Mbps, since my laptop support MIMO wifi too on windows I get over 200 mbps but i just stuck around ~80s mbps on Ubuntu
I wonder if I did anything wrong, here is what i get from **lspci -v**

```
07:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 3000 [size=256]
    Memory at a4204000 (64-bit, non-prefetchable) [size=4K]
    Memory at a4200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169
```

Thank you so much

---

### Post by chili555 on 2018-10-18
> 07:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet ControllerThis is ethernet, not wireless. Please check again.

---

### Post by ryuushen on 2018-10-18
```
00:14.3 Network controller: Intel Corporation Device a370 (rev 10)
    Subsystem: Intel Corporation Device 0034
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a4410000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi


```
I'm sorry, is it this one?
And thank you for replying

---

### Post by chili555 on 2018-10-19
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

---

