---
title: "Unreliable wired networking after installing gutsy kernel"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by Dropbear on 2007-08-31
I recently upgraded to the gutsy development kernel and am having difficulties accessing the network.  I only seem to be able to successfully get a connection about once every 3 restarts. Otherwise the network manager just spins continually trying to request an address from the network. It seems if I shutdown and start after about a minute it will connect. It is a very annoying weird problem which is now also happening with the feisty kernel. I connect with dhcp through a Thompson Speedtouch 530 router and have not changed any settings prior to this problem. ](*,)

---

### Post by noob12 on 2007-08-31
Can you show what kind of wired card do you have?

```

lspci -nn

```

---

### Post by Dropbear on 2007-08-31
```
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 PCI Express Bridge [10de:0247] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)

```

it uses the forcedeth driver

---

### Post by noob12 on 2007-08-31
You probably should file a bug, but have you checked your dmesg for any weirdness in the cases when it wasn't working?

---

### Post by tact on 2007-08-31
Hey there, another aussie huh!   

How did you update to the gutsy kernel, the process?   Was it JUST the kernel you updated?   Or did you deliberately or inadvertently also update some packages?

If you only updated the kernel and no packages then reverting to the older kernel should have you on exactly the same playing field as before the kernel upgrade.

If networking is now not working properly even when you revert to the older kernel - not working as it did before I mean - that kinda suggests that some packages other than kernel only were updated.  Need to find what changed and try to go back.

---

### Post by Dropbear on 2007-09-01
Looking through synaptic the only package which could possibly be causing the problem based on coming from the gutsy repository may be libc6. But to force the feisty version would mean removal of the gutsy kernel.
  I thought the problem may be a simple network setting. I've certainly tried a lot of them. As Ubuntu doesn't require frequent restarts it's something I can live with for now as networking works every
 time from a cold start.

---

### Post by noob12 on 2007-09-01
In your warm boots are you dual booting from Windows?

When you have problems do you have a link light, does **sudo ethtool eth0** (or whichever interface) show a link detected?

---

