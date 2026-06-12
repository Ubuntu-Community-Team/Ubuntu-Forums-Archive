---
title: "Linksys N300 AE1200 Wireless adapter/Ubuntu 12.04.4 LTS"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by kshannon6487 on 2014-05-13
My computer will not detect the new wireless adapter. I have it set up to a wired connection so I can currently use the internet.

I am new to ubuntu so not sure if it is a new driver I need.

```

[FONT=arial]kernel: 3.2.0-56-generic x86_64[/FONT]

[FONT=arial]lsusb: Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235][/FONT]
[FONT=arial]Bus 002 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
[/FONT]
```

---

### Post by kshannon6487 on 2014-05-13
I followed these directions:


[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER][COLOR=#777777]1[/COLOR]down vote[/CENTER]
[/TD]
[TD="class: answercell, bgcolor: transparent"]I just bought the Linksys AE1200 USB Wireless adapter and it works fine *19-Oct-2012*.
My lsusb results:
[INDENT]Bus 001 Device 005: ID 13b1:0039 Linksys AE1200 802.11bgn Wireless Adapter [Broadcom BCM43235]
[/INDENT]For some reason, the **Win XP driver on the installation CD would not work**. None of the other broadcom chipset drivers that I attempted worked for me either.
[h=3]The solution[/h]So, a search of here and Ubuntuforums yielded this link: [http://www.wikidevi.com/wiki/Linksys_AE1200](http://www.wikidevi.com/wiki/Linksys_AE1200)and provided this repaired version of the xp driver:[http://wikidevi.com/files/Drivers/Broadcom/bcmwl_4323x.zip](http://wikidevi.com/files/Drivers/Broadcom/bcmwl_4323x.zip).

[LIST=1]
[*]Download the bcmwl_4323x.zip and extract (for my example to follow, my downloads directory)
[*]I opened a Terminal window:
[LIST]
[*]cd /Downloads/bcmwl_4323x/xp/
[*]:~/Downloads/bcmwl_4323x/xp$ sudo ndiswrapper -i bcmwlhigh5.inf
[*]sudo modprobe ndiswrapper
[/LIST]

[*]ndiswrapper -l yielded:
[/LIST]
[INDENT]bcmwlhigh5 : driver installed 
device (13B1:0039) present
[/INDENT]
[LIST]
[*]Exit Terminal window, unplug LAN cable, System Restart.
[*](Optional) If the USB Wireless card does not work after reboot, you may need to add **ndiswrapper**to your /etc/modules so that it loads ndiswrapper at startup.
[LIST]
[*]You should be able to test if this is needed if upon boot, the LED on your wireless card is not lit. You run in terminal sudo modprobe -r ndiswrapper | sudo modprobe ndiswrapperand then the LED turns on.
[/LIST]
[/LIST]

[/TD]
[/TR]
[/TABLE]


From this thread: [http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter](http://askubuntu.com/questions/100090/how-do-i-install-the-driver-for-my-linksys-ae1200-wireless-n-usb-adapter)


It worked and it says my driver is installed succesfully. I rebooted and it will not locate any wireless connections. This PC I am on now is currently connected to that wireless network so I cannot figure out the problem. Any advice would be appreciated.

---

### Post by kshannon6487 on 2014-05-13
I booted it up without wired connection. It told me upon booting that wireless connections are available but I cannot seem to find any of them.

---

### Post by pdc on 2014-05-14
so the Ubuntu support page for Broadcom takes one to this [http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211) for your 43235

this seems to be the page for you

they seem to say the 43235 needs the brcmfmac (USB) driver: 

they say: ..the brcmfmac driver requires firmware that need to be separately downloaded. Firmware is available from the Linux firmware repository at: git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git 

I see there is already some firmware (se thumbnail) in lib/firmware/brcm but none for the 43235

---

