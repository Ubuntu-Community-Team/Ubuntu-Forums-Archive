---
title: "Edimax 7811Un WLAN adapter not working in Ubuntu 14.04.3"
date: 2016-01-18
forum: Networking &amp; Wireless
---

### Post by Michael_Kim on 2016-01-18
Hello,

I have a very old HP 625 notebook. It actually has WLAN, but it seems to be broken. The network controller is Broadcom BCM4313 (14e4:4727 rev 01). It does not work in Windows 7 and Ubuntu 14.04.3.

But I bought the Edimax 7811Un WLAN adapter which works fine on Windows 7, but on Ubuntu it says that the hardware switch is disabled. I installed the Realtek driver according to following post, but it did not work: [https://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](https://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

In the network settings of Ubuntu, the WLAN adapter is listed, but I can't seem to turn Wireless on.

The rfkill list command outputs the following message:
```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Please tell me if there is anything that I can do for this to work...

Edit: Oh, and the command rfkill unblock all did not wield any results, either. I have been trying to find a solution for a long time...

---

### Post by Michael_Kim on 2016-01-20
Please tell me why nobody is helping me. I know questions like this has been asked a lot, I have read a lot of them, but none of those threads helped me get my WLAN to work. I have tried all the suggestions that I have found on the Internet prior to asking in this forum. Please help me! Thanks!

---

### Post by Vladlenin5000 on 2016-01-20
Please find and use the WiFi toggle button. It shows hard blocked, i.e., it has been turned off by some _physical_ switch.

---

### Post by Michael_Kim on 2016-01-21
Like I wrote above the WLAN hardware from Broadcom on my notebook seems to be broken. That is why I am using the WLAN adapter from Edimax to go to the Internet on Windows 7 which works fine. But now I am trying to get the WLAN adapter to work on Ubuntu 14.04.3. Please tell me what I need to do to get the WLAN adapter to work, not the WLAN on my notebook. Thanks!

---

### Post by Vladlenin5000 on 2016-01-21
Most laptops do NOT distinguish between internal (miniPCIe) or external (USB) in what concerns the on/off button. First of all turn it on and check whether or not you can now select and connect to a network with the USB dongle.

---

### Post by Michael_Kim on 2016-01-22
There does not seem to be a physical switch on my notebook to turn wifi on. To be sure I tried the battery trick that I found on the Internet to turn the hardware switch on (holding the power button for 30 seconds without the battery inside). It did not work.

Also, I have set up a multi-boot system on my notebook. It has both Windows 7 and Ubuntu on it, and like I said I have no problem using wifi on Windows 7. I want to know why it does not work on Ubuntu.

Why do I need to turn on the hardware switch on my notebook when I am using a WLAN adapter which does not have a hardware switch? I mean, why is something that is working on Windows not working in Linux? That is really frustrating... :(

---

### Post by Michael_Kim on 2016-01-22
It is working now!! I reset the BIOS (like in the [youtube video]("https://www.youtube.com/watch?v=eB2-oaePlKc")), and the wifi of my notebook (Broadcom) is working again! No need for a WLAN adapter! Thanks for the help until now.

---

