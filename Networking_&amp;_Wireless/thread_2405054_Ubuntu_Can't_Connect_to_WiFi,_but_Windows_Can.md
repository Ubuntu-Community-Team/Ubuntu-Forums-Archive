---
title: "Ubuntu Can't Connect to WiFi, but Windows Can"
date: 2018-10-31
forum: Networking &amp; Wireless
---

### Post by geeky-1 on 2018-10-31
My laptop won't connect to my work wifi (either internal or external) from Ubuntu 18.04.1 LTS, but when I reboot it to Windows 10, it connects to the wifi. I'm able to connect to both internal and external wifi with 2 Android phones. I also have no problems connecting to my home wifi with this laptop running Ubuntu.

I tried mirroring my phone settings as close as possible, although there are several wifi security settings in Ubuntu that I don't see on my phones. I also tried all combinations of the settings without success. Anybody know why it's failing to connect?

---

### Post by howefield on 2018-10-31
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by geeky-1 on 2018-11-09
I was running out of space on the root drive, so reinstalled Ubuntu 18.04 LTS, and I still can't connect to the wifi at work.

---

### Post by strixtux on 2018-11-09
It might help if you supplied a few details about your hardware.

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

 > **Wireless connection troubleshooter**

 **Check that the wireless adapter was recognize**
 
   Even though the wireless adapter is connected to the computer, it may not   have been recognized as a network device by the computer. In this step, you   will check whether the device was recognized properly.
 
[LIST]
[*]Open a Terminal window, type ```
lshw -C network
``` and press       Enter. If this gives an error message, you may need to install       the lshw program on your computer. 
[*] Look through the information that appeared and find the Wireless       interface section. If your wireless adapter was detected properly,       you should see something similar (but not identical) to this:
 ```
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
``` 
[*] If a wireless device is listed, continue on to the       [Device Drivers       step]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-device-drivers.html.en").
 If a wireless device is not listed, the next steps you take       will depend on the type of device that you use. Refer to the section       below that is relevant to the type of wireless adapter that your computer       has ([internal PCI]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html.en#pci"), [USB]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html.en#usb"),       or [PCMCIA]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html.en#pcmcia")). 
[/LIST]


Reference site: [https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html.en)

Regards,
Mitesh

---

### Post by geeky-1 on 2018-11-13
Well, I'm connected to my home wifi to read this so I doubt it's not recognizing my wireless adapter, but the info is below, however I don't see any drivers in the docs for Intel 8265/8275:
```

01:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)
    Subsystem: Intel Corporation Wireless 8265 / 8275
    Flags: bus master, fast devsel, latency 0, IRQ 129
    Memory at d1100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```

---

### Post by geeky-1 on 2019-03-07
A few security "experts" I talked to all thought it was because my drivers were out of date, which didn't make sense as I had the latest version of Ubuntu installed. I finally was able to ask a Linux person at work and he told me it was because they only support Windows security for wifi and I could hack it to get it to work with Linux, but it would take me like a month of hacking. Stupid as they use Linux file servers and Samba so our Windows PCs can browser the servers.

---

### Post by wildmanne39 on 2019-03-07
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone should be able to help you.

---

### Post by azwar on 2019-03-07
Can you run ifconfig and iwconfig command then paste the output here. It would help us get more details for your problem.

---

