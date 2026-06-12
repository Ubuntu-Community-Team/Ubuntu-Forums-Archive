---
title: "sometimes ubuntu does not see the wireless card"
date: 2020-05-14
forum: Networking &amp; Wireless
---

### Post by lucio-messina-w on 2020-05-14
Hi all,
I have an old PC on which I installed Ubuntu 16.04. The wireless had worked perfectly for ages but recently something strange started happening: when I turn on the PC sometimes Ubuntu cannot see the wireless card. Other times the WIFI works but I'm not doing anything different: this is a (apparently) random failure.

I managed to run the [wireless-script]("https://github.com/UbuntuForums/wireless-info") (not sure if it was the last version, I'm sorry) twice:
A) while the wireless was working fine; and
B) while it was not working

This produced the two reports that I attach to this post: [ATTACH]285862[/ATTACH] and [ATTACH]285863[/ATTACH].

There are many information on the system and networking status, but I think the most relevant one is that when the WIFI is not working ```
lspci
``` cannot see the Wireless Network Adapter (Qualcomm Atheros AR9485):

From the report with working WIFI:
```

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    DeviceName: Atheros AR9485 802.11b/g/n WiFi Adapter
    Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter [103c:1838]

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:193b]


```

From the report with not working WIFI:
```

##### lspci #############################

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:193b]


```

And then consequently the output of many other commands are incomplete (rfkill, lsmod, ifconfig and so on).

Can someone help me to solve the problem?
Thank you in advance.

---

### Post by crip720 on 2020-05-14
Don't know enough to help, but maybe point to direction.  One reason might be an updated wifi driver that is the problem, solution would be to install older driver.  Had that with a wired driver.  Second reason would wifi card has loose connection or is dying.  The updated wired driver I had would only work if cable was plugged in after booting, older driver no problems.  First reason is my bet.

---

### Post by praseodym on 2020-05-14
Check the BIOS/UEFI settings if wireless is turned on all the time. SecureBoot is disabled?

---

### Post by lucio-messina-w on 2020-05-15
> **crip720 said:**
> Don't know enough to help, but maybe point to direction.  One reason might be an updated wifi driver that is the problem, solution would be to install older driver.  Had that with a wired driver.  Second reason would wifi card has loose connection or is dying.  The updated wired driver I had would only work if cable was plugged in after booting, older driver no problems.  First reason is my bet.

Thank you for your reply. I did not update the drivers between the two runs of the wireless-script: the two reports were produced by running the script with the very same system settings, the first one while the wireless was working fine and the second one while it was not.
I cannot find the wifi driver name and version second report; I guess it is because the wireless card is not recognised at all.

[quote= 		praseodym]
Check the BIOS/UEFI settings if wireless is turned on all the time. SecureBoot is disabled? 		
[/quote]

I will check, thank you. SecureBoot is disabled as reported in both wireless-script outputs.

---

