---
title: "Wireless is disabled by hardware switch on a netgear usb adapter"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by accguy9009 on 2014-04-18
I just installed Xubuntu 14.04. My laptop is using a Netgear WG111v2 USB Wireless adapter. I have seen from several sources that the drivers have been built into the linux kernel since Ubuntu 9 for the netgear wg111v2. I have gotten this adapter working in the past on other distros but it required use of the NDIS Wrapper. During install I was asked for my wifi password which I provided. At first boot I saw an icon at top of screen and cursor showed my Netgear WG111v2 adapter but greyed out it says "Wireless is disabled by hardware switch". Since this is a USB adapter something is amiss. I booted into UBUNTU 14.04 live and get same thing. I see on web others have had this in past. I try from terminal rfkill unblock all. I also try sudo rfkill unblock wifi. then reboot and go to settings/network connections and the only option listed is wired connection 1. So I click +Add/choose connection type/wifi/create. Asked for SSID and I enter it. Mode: has Infrastructure and drop down has ad-hoc. another tab has wifi security, I put in WPA2 personal and enter password but the save button is greyed out, can't save. I wasn't expecting these obstacles for a wifi adapter with drivers built in to kernel. It seems the wifi adapter is still disabled. the adapter works great in Windows 8.1/8/7/Vista. I did get it working several years back in Suse 12. I saw somewhere the network manager was buggy and I should uninstall it and replace it with a different one. Was so looking forward to using 14.04 just wanted the xfce desktop. Any help? Thks in advance. Ethernet works  fine and Enable Networking is checked. Underneath the Enable Wi-Fi is greyed out so I can't enable it.

---

### Post by praseodym on 2014-04-18
Hi,

what kind of computer is it (brand, model)? Please show the terminal outputs of
```

lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by accguy9009 on 2014-04-18
the laptop is a lenovo IdeaPad Y430. In the interest of full disclosure when I was given this laptop after replacing the hard drive I have never been able to get the on board wifi Intel WiFi link 5100 AGN to work. It thinks it is turned off but flipping the switch and the fn key never turns it on but the device manager in Windows says latest drivers installed. I always used the USB Netgear WG111v2 for wifi purposes as a result. Tried many times in Windows gave up. The Intel WiFi link 5100 AGN is also listed as disabled by hardware switch. On diff laptop now will run those commands in a bit and post the results here, thx

---

### Post by monkeybrain20122 on 2014-04-18
> **accguy9009 said:**
> the laptop is a lenovo IdeaPad Y430. In the interest of full disclosure when I was given this laptop after replacing the hard drive I have never been able to get the on board wifi Intel WiFi link 5100 AGN to work. It thinks it is turned off but flipping the switch and the fn key never turns it on but the device manager in Windows says latest drivers installed. I always used the USB Netgear WG111v2 for wifi purposes as a result. Tried many times in Windows gave up. The Intel WiFi link 5100 AGN is also listed as disabled by hardware switch. On diff laptop now will run those commands in a bit and post the results here, thx

I don't know about the usb netgear, but your internal Intel 5100 AGN should work if you install the firmware
[http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi)

---

### Post by accguy9009 on 2014-04-18
I will try that but the built in wifi is turned off and never turns on when i flip the switch or use fn key. the fn keys do work for other purposes. Right now enable wifi is greyed out and neither adapter the intel or netgear can be used. I have tried many times to get it working in windows with no luck. i see others have this issue in different distros having wifi disabled by hardware switch i think it is an rf kill issue but i am out of my depth in this OS i just know the netgear adapter is supported natively in Ubuntu and it works in Windows, thks.

---

### Post by monkeybrain20122 on 2014-04-18
Wifi may be disabled in BIOS, have you checked that?

---

### Post by accguy9009 on 2014-04-18
Great minds think alike. Tried that long ago. The bios is very limited to say the least and nothing in there lets you turn wifi on or off

---

### Post by praseodym on 2014-04-18
> **monkeybrain20122 said:**
> Wifi may be disabled in BIOS, have you checked that?

Right, check these steps:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by accguy9009 on 2014-04-18
The hard reset did not work. I may try another network manager. What other network manager should i try and how to delete the native one?

---

### Post by praseodym on 2014-04-19
Did you try
```

sudo rfkill unblock all
```
Please show afterwards
```

rfkill list
lsmod
iwconfig
```

---

### Post by accguy9009 on 2014-04-19
Thanks all for your kind help and support. I never had any expectations that my on board wfi would work on this Lenovo. It has been turned off since I got this laptop after several people made efforts to use it. I got it working well, replaced hard drive, optical drive and it works great in dual monitor on 50" TV using HDMI and the Netgear USB wifi adapter. It is used to stream music and video from external drive and for XBMC. I just expected to be able to use the USB wifi adapter since the drivers are included in the kernel. was excited about the LTS. I am not a Win 8.1 hater got it working perfectly for XBMC so gonna stay there for now. just don't have the time to wrestle with the wifi issues atm but will look at this again when i do. i don't have wired ethernet in this room or i would be using it. great community here and best to all. Had same exact issues on Mint

---

### Post by praseodym on 2014-04-19
You can also try:
```

pressing the button/key combination permanently during boot-up
pressing the button/key combination repeatedly during boot-up
```

---

