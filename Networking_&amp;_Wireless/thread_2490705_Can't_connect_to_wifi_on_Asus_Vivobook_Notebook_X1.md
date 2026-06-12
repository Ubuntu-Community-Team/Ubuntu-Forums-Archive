---
title: "Can't connect to wifi on Asus Vivobook Notebook X1504ZA-NJ205"
date: 2023-09-12
forum: Networking &amp; Wireless
---

### Post by roeesi on 2023-09-12
Hi! I bought a new Asus notebook and installed ubuntu on it, but I can't see the wifi icon I was used to seeing on my previous laptop that ran ubuntu, and so I can't connect to wifi.

I tried installing rtl8821ce-dkms as suggested in [another thread]("https://ubuntuforums.org/showthread.php?t=2451466") but the problem persists.

These command outputs may be helpful:

```

$ iwconfig
lo        no wireless extensions.


```


```

$ lspci
0000:00:00.0 Host bridge: Intel Corporation Device 4601 (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation Device 46a8 (rev 0c)
0000:00:04.0 Signal processing controller: Intel Corporation Alder Lake Innovation Platform Framework Processor Participant (rev 04)
0000:00:06.0 System peripheral: Intel Corporation Device 09ab
0000:00:08.0 System peripheral: Intel Corporation 12th Gen Core Processor Gaussian & Neural Accelerator (rev 04)
0000:00:0a.0 Signal processing controller: Intel Corporation Platform Monitoring Technology (rev 01)
0000:00:0e.0 RAID bus controller: Intel Corporation Volume Management Device NVMe RAID Controller
0000:00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01)
0000:00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01)
0000:00:15.0 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 (rev 01)
0000:00:15.1 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #1 (rev 01)
0000:00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation Device 51b8 (rev 01)
0000:00:1c.6 PCI bridge: Intel Corporation Device 51be (rev 01)
0000:00:1f.0 ISA bridge: Intel Corporation Alder Lake PCH eSPI Controller (rev 01)
0000:00:1f.3 Audio device: Intel Corporation Alder Lake PCH-P High Definition Audio Controller (rev 01)
0000:00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01)
0000:00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01)
0000:02:00.0 Network controller: MEDIATEK Corp. Device 7902
10000:e0:06.0 PCI bridge: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #0 (rev 04)
10000:e1:00.0 Non-Volatile memory controller: Intel Corporation SSD 660P Series (rev 03)

```

 Thanks!

---

### Post by chili555 on 2023-09-13
> Network controller: MEDIATEK Corp. Device 7902We need more information. Please run and post:

```
lspci -nnk | grep 0280 -A3
```

> I tried installing rtl8821ce-dkms as suggestedThere is no Realtek device in your lspci listing so it won't be useful. I suggest that you remove it.

I suspect this will be the result: [https://askubuntu.com/questions/1467679/wifi-and-bluetooth-dont-function-on-asus-vivobook-15-in-ubuntu-23-04](https://askubuntu.com/questions/1467679/wifi-and-bluetooth-dont-function-on-asus-vivobook-15-in-ubuntu-23-04)

> It seems the card is not supported:

---

### Post by roeesi on 2023-09-15
> 
We need more information. Please run and post:

```

lspci -nnk | grep 0280 -A3 


```


Here it is:

```

0000:02:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7902]
    DeviceName: WLAN
    Subsystem: AzureWave Device [1a3b:5520]
10000:e0:06.0 PCI bridge [0604]: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #0 [8086:464d] (rev 04)

```

Also, my wireless info is in [https://paste.ubuntu.com/p/VpxVPMYHDf/](https://paste.ubuntu.com/p/VpxVPMYHDf/)
> 
I suspect this will be the result: [https://askubuntu.com/questions/1467...n-ubuntu-23-04]("https://askubuntu.com/questions/1467679/wifi-and-bluetooth-dont-function-on-asus-vivobook-15-in-ubuntu-23-04")

[QUOTE]It seems the card is not supported:[/QUOTE]
Does it mean that there is no way to connect to wireless networks from Linux using this card and I have to either replace it or connect to an external wifi device or smartphone?

---

### Post by chili555 on 2023-09-15
It means there is no way yet. I am sure a working driver will appear soon. In the meantime there are many fully supported USB wireess devices available. Please consult the stickie at the top of the forum.

---

### Post by roeesi on 2023-09-15
> **chili555 said:**
> I am sure a working driver will appear soon.
What do you mean by "soon"? Months? Years? The thread you linked to is 4 months old and it seems there is still no driver for this adapter.
Also, how can I know when there is one?
Thanks!

---

### Post by chili555 on 2023-09-15
> What do you mean by "soon"? Months? Years? Possibly.

All I can tell you is that when manufacturers release new devices, the Linux driver comes along soon, typically less than a year. Mediatek is usually pretty quick about these things and I'm surprised that it has taken this long. 

I suggest that you file a bug report: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

You will know that a driver is available, first, when you google 14c3:7902, the pci.id for your device and you see results about github, compiling, etc. instead of, 'sorry, not supported yet.' You will also know that the driver is included in the main Ubuntu kernel when, after an update and the requested reboot, Network Manager has a list of networks, and offers to connect. If you are using a USB wireless at the time, NM will show two lists as you now have two wireless interfaces working.

I am sorry I haven't better suggestions.

---

### Post by kapi24542 on 2024-09-11
> **chili555 said:**
> Possibly.

All I can tell you is that when manufacturers release new devices, the Linux driver comes along soon, typically less than a year. Mediatek is usually pretty quick about these things and I'm surprised that it has taken this long. 

I suggest that you file a bug report: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

You will know that a driver is available, first, when you google 14c3:7902, the pci.id for your device and you see results about github, compiling, etc. instead of, 'sorry, not supported yet.' You will also know that the driver is included in the main Ubuntu kernel when, after an update and the requested reboot, Network Manager has a list of networks, and offers to connect. If you are using a USB wireless at the time, NM will show two lists as you now have two wireless interfaces working.

I am sorry I haven't better suggestions.

Hi!! how are you? There is some new here?
Thank you


PS:
inxi -n
Network:  Device-1: MEDIATEK driver: N/A

lspci -nn
01:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7902]

---

