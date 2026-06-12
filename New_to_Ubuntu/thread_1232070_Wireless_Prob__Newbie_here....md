---
title: "Wireless Prob / Newbie here..."
date: 2009-08-05
forum: New to Ubuntu
---

### Post by LinLou on 2009-08-05
Hello,

I have recently installed Ubuntu 9.04 on a HP Pavilion dv5-1012ea and i was wondering if there are any drivers that could help me on activating my wireless device and if so how can i install these. My wireless card is Intel® PRO/Wireless 4965AGN.

Thanks..

---

### Post by realzippy on 2009-08-05
[https://help.ubuntu.com/community/WifiDocs/SolvingWireless](https://help.ubuntu.com/community/WifiDocs/SolvingWireless)

---

### Post by Shig on 2009-08-05
Hi There

The intel 4965AGN should be handled by the iwlagn driver, which is included in recent versions of Ubuntu (definately in 9.04, which I am running).

If the wireless device is not showing up in NetworkManager, can you please run the following in a terminal and share the output with us?
```
dmesg | grep iwl
```

---

### Post by LinLou on 2009-08-05
ok.. This  [https://help.ubuntu.com/community/WifiDocs/SolvingWireless](https://help.ubuntu.com/community/WifiDocs/SolvingWireless) didnt help..
Although i found out that my card works on Linux ([http://www.ubuntuhcl.org/browse/product+intel-wireless-wifi-link-4965agn?id=6826](http://www.ubuntuhcl.org/browse/product+intel-wireless-wifi-link-4965agn?id=6826)). 

Any other suggestions??


The results where 

[   11.523140] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   11.523142] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   11.523198] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.523206] iwlagn 0000:02:00.0: setting latency timer to 64
[   11.523239] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   11.543393] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   11.543453] iwlagn 0000:02:00.0: irq 2294 for MSI/MSI-X
[   11.544326] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   22.526053] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   22.720953] iwlagn: Radio disabled by HW RF Kill switch

by using that on terminal.
dmesg | grep iwl

---

### Post by Majorix on 2009-08-05
I have the same wireless card and it works flawlessly with 9.04 and 9.10. However, you should be aware that the support for this card comes with the newer kernels (might be starting with 2.6.28 ).

---

### Post by LinLou on 2009-08-05
Just a reminder that i am using a HP Pavilion dv5-1012ea which does not have buttons except the keyboard. All the other buttons for activating the Wireless, Adjusting the volume and turning On/Off the PC are a touch screen where the only touch button that does not work is the one for activating the Wireless.

---

### Post by LinLou on 2009-08-05
Any other suggestions? solutions? please?

---

### Post by LewRockwell on 2009-08-05
> **LinLou said:**
> 

dmesg | grep iwl

[   22.720953] iwlagn: **Radio disabled by HW RF Kill switch**

**Radio disabled by HW RF Kill switch**

[http://ubuntuforums.org/showthread.php?t=616556](http://ubuntuforums.org/showthread.php?t=616556)

some machines have switches, some use the function keys, and still others use commands via touch screen and other input devices

.

---

### Post by LinLou on 2009-08-06
Not that helpful.. what i think i need, is me to be able to turn on/off the wireless without pushing a button.. and i mean not from the Bios.. is there any chance that this is possible?
:confused::confused:

---

### Post by realzippy on 2009-08-06
This  [https://help.ubuntu.com/community/WifiDocs/SolvingWireless](https://help.ubuntu.com/community/WifiDocs/SolvingWireless) didnt help..

...that link e.g. tells you about "iwconfig",what would tell you
your current wlan status..

sudo ifconfig yourdevice0 up 

would start it without button..

sudo ifconfig yourdevice0 down would....

---

### Post by LinLou on 2009-08-06
nope.. did not work that either..

---

### Post by realzippy on 2009-08-06
Do you have a windows partition?

---

### Post by LinLou on 2009-08-06
No.. full ubuntu 9.04.. the thing is that i tried to install the drivers of the wireless through the Windows Wireless Drivers <-Administration <-System but when i downloaded the drivers i got an .exe file and not a .inf file which is required..

---

### Post by Buuntu on 2009-08-06
Have you tried adding the already existing wireless network?  Just go to network manager and add a new wireless network.  Then the only thing you really need to put in is the SSID, which is the name shown in windows for the network.  

See it that helps.

---

### Post by LinLou on 2009-08-06
:(:( No it didnt help.. still the same.. the thing is that my wireless is disabled.. i think that my first priority is to enable it..

---

### Post by Buuntu on 2009-08-06
Ok then, try following this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Shig on 2009-08-07
Some people have had luck with toggling the wireless switch (it seems different model notebooks seem to have this problem in newer version of Ubuntu) and then reloading the driver. Should only have to do it once to enable the wireless. Other people have had to load up windows, enable the wireless, and then it stays enabled for use in Ubuntu: [Check out this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269264")

You could also try using update-manager to download the latest Kernel, which [this]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970") bug report suggests fixes the issue with rfkill too.

---

