---
title: "[SOLVED] A different type of Atheros problem..."
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by apetresc on 2007-09-08
So I am trying to fix this Toshiba laptop; it appears to have an Atheros card according to lspci: ```
cc@Kocharon:~$ lspci | grep Atheros
04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
```
However, unlike the multitude of other Atheros-related problems, I can't even get a fresh install of Ubuntu to see the interface. For example, ```
cc@Kocharon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
(eth0 is the wired connection, which works.)
The strange part is that the restricted-modules package is installed, and in fact the Restricted Drivers Manager does see (and has enabled) the "Atheros Hardware Access Layer", but still nothing. There is no ath0 interface visible anywhere.\

When I grep dmesg for relevant output, I find only ```
cc@Kocharon:~$ dmesg | grep ath
[   16.300000] ath_hal: module license 'Proprietary' taints kernel.
[   16.304000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   16.520000] ath_pci: 0.9.4.5 (0.9.3.1)
```

Hopefully someone here has an idea :) Thanks in advance!

---

### Post by spd106 on 2007-09-08
Try grepping through dmesg again for hal. If it return status 13, then it's likely that the chipset isn't supported by the binary firmware version you have. Then you have few options, the most likely to work would be ndiswrapper. If you are feeling bold, you could try using a newer madwifi version from svn. See [madwifi.org](http://madwifi.org) for more information.

---

### Post by apetresc on 2007-09-08
Thanks for your reply, spd106. 
I should have though of that earlier; but I had only grepped for 'hal', not 'HAL'. Now that I grep for the uppercase version, I get
```
cc@Kocharon:~$ dmesg | grep HAL
[   16.436000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
```
So I guess the diagnosis is complete now. Before compiling from SVN (that's not a problem, I can do that, but it's inconvenient), I will try the Gutsy Tribe 5 LiveCD and see if perhaps the MadWifi version there supports this chipset. Is there any chance, or do they both use the same version?

Thanks for your help so far, spd106! If I have any further problems I will post them in this thread.

---

### Post by apetresc on 2007-09-08
Sorry for the double-post, but new stuff now. I tried building from svn, and the compilation went well. When I reloaded all the modules, it seemed to work, but dmesg reports ```
cc@Kocharon:~$ dmesg | tail
[  125.060000] ath_hal: driver unloaded
[  148.024000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[  148.040000] wlan: 0.8.4.2 (svn r2702)
[  148.048000] ath_pci: 0.9.4.5 (svn r2702)
[  148.048000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
[  148.048000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[  148.048000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[  148.052000] MadWifi: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
[  148.052000] ACPI: PCI interrupt for device 0000:04:00.0 disabled
[  154.568000] ath_rate_sample: 1.2 (svn r2702)
```

It is, at least, a different HAL status error from before, but I'm not sure where to go from here. Hopefully someone's overcome this before. Thanks in advance :)

---

### Post by apetresc on 2007-09-08
Okay, I solved the problem using a different method; I gave up on MadWifi and went with ndiswrapper, using the script on this thread: [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

Hope this helps someone else.

---

