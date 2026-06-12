---
title: "Fail to resume and no wireless after overnight suspend"
date: 2015-12-07
forum: Networking &amp; Wireless
---

### Post by SoftVision on 2015-12-07
I have an ASUS ZenBook UX305 laptop running Ubuntu 15.10. I had this same problem with Ubuntu 14.04 as well. I have got my wireless working now but I have to reset it somehow every day. When I leave my laptop closed to suspend overnight and wake up the next morning, the power light comes back on but there is no response from the display (no backlight). I don't know whether the backlight failed to resume from the suspend or the whole system. I hold the power button down to reboot and when I get back into Ubuntu, there is no wireless device available. 

This is what I normally get:
```
lspci -k

00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 181d
	Kernel driver in use: bdw_uncore
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 181d
	Kernel driver in use: i915
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 181d
	Kernel driver in use: snd_hda_intel
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 181d
	Kernel driver in use: proc_thermal
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 201f
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 181d
	Kernel driver in use: mei_me
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 181d
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
	Kernel driver in use: pcieport
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 181d
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 181d
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 181d
[B]02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7265
	Kernel driver in use: iwlwifi[/B]

```

But when this problem happens every day, those last three lines in bold don't show up. I also tried "sudo rfkill list all" but that would only list my Bluetooth device. The only thing that makes my wireless work is to go into the BIOS and fiddle with different settings. Sometimes it works if I just reset BIOS settings to default, sometimes I just toggle the "Network Stack" option which is Disabled by default. Today I disabled "Fast Boot" and that seemed to work. I don't know why this keeps happening really.

I have tlp installed with the default settings, but I have also previously used laptop-mode-tools. The problem occurred even then. I'm not sure if it's anything to do with these power management tools but I haven't found other users of this laptop report such an issue with these tools. This problem only occurs if I leave the laptop lid closed to suspend overnight. There are no problems if I go away for about 30 minutes and try to resume it.

```
uname -r

4.2.0-19-generic

```

I would be happy to provide any logs or output based on your suggestions, I'm just not sure what to check right now. I would appreciate any help with this! :D

---

