---
title: "CLEVO W740SU WiFi connection"
date: 2015-03-02
forum: Networking &amp; Wireless
---

### Post by Dino_Jakolis on 2015-03-02
Hello everyone!

First of all, I am a complete Ubuntu noob who has decided to fully switch to it and leave behind years and years of Windows experience. Like I might have guessed, the learning curve will be happening and it will not be easy. But, it wouldn't be fun if it was, right?

Alright, so I have installed Ubuntu 14.10 64-bit along with Google Chrome directly from Google website downloads. After that I ran software update and let it complete its job. After the update was finished, I randomly select a song on YouTube to see if sound and video are good and after clicking full-screen mode, I got the black screen. Restarted laptop using power button for 3 seconds. Since then, I am not picking up any WiFi networks. I am using my phone as a tethering device and I have Internet on laptop via Bluetooth. 

It would be great to hear any advice on this matter. 

Also, since I am completely new to Ubuntu, do you advise me to open a new thread on how to setup my laptop with all the drivers and other possible things to have it run silky smooth?

Thanks, 

Dino

---

### Post by ajgreeny on 2015-03-03
What graphics card has the laptop got and what wifi card?
Let's see the output of ```
lspci
```
You may need to install drivers for one or other of those two hardware items.

---

### Post by Dino_Jakolis on 2015-03-03
Graphics card: Intel Iris Pro Graphics 5200
Wireless card: Realtek RTL8723AE

```
00:00.0 Host bridge: Intel Corporation Crystal Well DRAM Controller (rev 08)00:02.0 VGA compatible controller: Intel Corporation Crystal Well Integrated Graphics Controller (rev 08)
00:03.0 Audio device: Intel Corporation Crystal Well HD Audio Controller (rev 08)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter



```

---

### Post by Bucky Ball on 2015-03-03
> **Dino_Jakolis said:**
> 

Also, since I am completely new to Ubuntu, do you advise me to open a new thread on how to setup my laptop with all the drivers and other possible things to have it run silky smooth?


Welcome. Yes. Please open a new thread for anything that is not related to your wifi issue. 

This may not be a problem with drivers, though, as your graphics and wifi were working previously by the sounds of it. So, you already have all drivers you need installed if everything was working before.

Incidentally, hard shutdown with the power button is not ideal. If you hit a black screen, hold control+alt and hit F1. This should take you to a tty (like a giant, full screen terminal). Login there and then:

```
sudo reboot -h now
```

That will warm boot the machine. Much healthier for the hardware. ;)

---

### Post by Dino_Jakolis on 2015-03-03
> **Bucky Ball said:**
> Welcome. Yes. Please open a new thread for anything that is not related to your wifi issue. 

This may not be a problem with drivers, though, as your graphics and wifi were working previously by the sounds of it. So, you already have all drivers installed if everything was working before.

Thank you!

Correct. Everything worked right out of the box. There were no additional driver updates. However, I did notice when scrolling, I get that 'v-sync tearing' effect if you can understand me.

Edit: I tried "sudo reboot -h now" command in the tty now, but that did not help with the WiFi. Thanks though. I will write it down for future events. Still unable to pick up WiFi networks...

Edit #2: Had some work to do around house so I shut down the laptop. Turned it on later and WiFi works. Great! I guess those commands did help after shut down option rather than restart?

---

