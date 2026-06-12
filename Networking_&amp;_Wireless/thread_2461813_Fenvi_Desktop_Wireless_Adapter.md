---
title: "Fenvi Desktop Wireless Adapter"
date: 2021-05-07
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2021-05-07
Hey all,  I just bought this Fenvi FV-AX3000 upgrade and I was so excited to get it for the price I did I forgot to check the compatibility.  It connects via PCI,-E, 802.11 ax,/ac/a/b/g/n, double frequency, 2.4Ghz and 5Ghz and compatible with Windows 10 64bit.  I just figured I'd easily be able to find a Linux driver for it, but after a search of 2 pages on Duckduckgo I cannot find anything.  Does anyone no about this adapter or wher I can find the driver?

Thanks

---

### Post by chili555 on 2021-05-07
Let's find out a bit more about the device. Please run and post the result of the terminal command:

```
lspci -nnk | grep 0280 -A3
```Thanks.

---

### Post by shane_faulkinbury2 on 2021-05-07
Should I unplug my old adapter and install the new one first?

---

### Post by chili555 on 2021-05-07
> **shane_faulkinbury2 said:**
> Should I unplug my old adapter and install the new one first?Yes, please.

I'd also like to see:

```
uname -r
sudo dmesg | grep iwl
```

---

### Post by shane_faulkinbury2 on 2021-05-07
I actually don't thiink it's plugged in right or there's problem with it.  I can't get it working on Windows 10 either.  Plus, no bluetooth!

[CODE]lspci -nnk | grep 0280 -A3fake@fake-OptiPlex-30201635AO05A8:~$ uname -r
5.8.0-50-generic
fake@fake-OptiPlex-30201635AO05A8:~$ sudo dmesg | grep iwl
[sudo] password for fake:
fake@fake-OptiPlex-30201635AO05A8:~$[CODE]

---

### Post by chili555 on 2021-05-07
> I actually don't thiink it's plugged in right or there's problem with it. I agree. Please try reseating it and check the BIOS/EFI to see if there is a setting to enable/disable wireless.

---

### Post by shane_faulkinbury2 on 2021-05-08
Get this, it wasn't plugged in right.  I opened up my case, secured the cords, didn't install a driver and everything is working!

[CODE# lspci -nnk | grep 0280 -A303:00.0 Network controller [0280]: Intel Corporation Wi-Fi 6 AX200 [8086:2723] (rev 1a)
	Subsystem: Intel Corporation Wi-Fi 6 AX200 [8086:0084]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
root@fake-OptiPlex-30201635AO05A8:/home/fake# uname -r
5.8.0-50-generic
root@fake-OptiPlex-30201635AO05A8:/home/fake# sudo dmesg | grep iwl
[   13.336973] iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
[   13.723269] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-cc-a0-56.ucode failed with error -2
[   14.700833] iwlwifi 0000:03:00.0: api flags index 2 larger than supported by driver
[   14.700842] iwlwifi 0000:03:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.22
[   14.700844] iwlwifi 0000:03:00.0: Found debug destination: EXTERNAL_DRAM
[   14.700845] iwlwifi 0000:03:00.0: Found debug configuration: 0
[   14.701061] iwlwifi 0000:03:00.0: loaded firmware version 55.d9698065.0 cc-a0-55.ucode op_mode iwlmvm
[   14.701917] iwlwifi 0000:03:00.0: Direct firmware load for iwl-debug-yoyo.bin failed with error -2
[   17.042145] iwlwifi 0000:03:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[   17.223427] iwlwifi 0000:03:00.0: base HW address: c8:e2:65:06:6d:1e
[   17.378777] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
root@fake-OptiPlex-30201635AO05A8:/home/fake# 


][CODE]

---

### Post by chili555 on 2021-05-08
Awesome! Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by shane_faulkinbury2 on 2021-05-08
I didn't check it close enough.  The top code says [CODE and the bottom is ][CODE]

---

