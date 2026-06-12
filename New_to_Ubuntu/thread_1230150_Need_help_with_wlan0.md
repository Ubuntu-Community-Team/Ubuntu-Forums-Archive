---
title: "Need help with wlan0"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by bgivens33 on 2009-08-03
I was running 7.10 fine with my wireless card and then I upgraded to 9.04 and I can't seem to get it to work.  It's a wg311v3 pci card.  Here are some of my outputs-

lspci-

```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)

```


ndiswrapper -l

```
wg311v3 : driver installed
	device (11AB:1FAA) present
```

I've read countless threads and can't seem to find the right answer.  Thanks in advance.

---

### Post by bgivens33 on 2009-08-03
bump.

---

### Post by jocampo on 2009-08-03
Follow this nice troubleshooting guide

[http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

Once done, you can re-post your link at: [http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336") That's the Network and Wifi sub-forum. Maybe posting in a more specialized forum you'll get more help.

---

### Post by bgivens33 on 2009-08-03
awesome... thanks.

---

