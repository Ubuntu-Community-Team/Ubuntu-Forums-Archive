---
title: "hardware in 11.04 not right"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by bob brazie on 2011-05-16
After a fresh install of 11.04 on a 3 year old Acer Extensa 4420 Natty ran just fine for the first three boots using the Unity desktop.

On the next boot there was a warning that the machine did not have the right hardware to run Unity and I should choose to boot into the "classic" Ubuntu. Which it booted into on it's own even though "Ubuntu" was selected in the login screen settings. It would still boot to the "classic" on several boot try's even though "Ubuntu" was selected and not "classic"

Can anyone help here or if not what is the Ubuntu "launchpad" site address to ask this question.

Thanks in advance. Bob

---

### Post by mikewhatever on 2011-05-17
Would it be possible for you to provide the model of the graphics card. That info seems to be essential, and yet, there is no mention of it in your post.
One might guess that your card was deemed to be problematic with the new interface, and therefore, it may have been blacklisted by an update. If that's the case, there is a way to circumvent the blacklisting, butplease provide the requested info first.
If you don't know anything about the card, just post the output of **lspci -nn** from a terminal window.

---

### Post by bob brazie on 2011-05-17
Sorry, I didn't know the command. Strange but every so many boots it does boot into Unity.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

bob@bob:~$ lspci-nn
lspci-nn: command not found
bob@bob:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
0b:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller [1217:7136] (rev 01)
0b:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0b:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
0b:06.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
bob@bob:~$

---

### Post by mikewhatever on 2011-05-17
Thanks for the output. Here is the line that corresponds to your graphics card:
> 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]

There are several users with the same card, also having problems with Unity/Compiz in Natty, but after a quick look through those threads I haven't seen solutions. All I can suggest for now is using Gnome2 with no effects or, if you need Compiz, reverting to one of the earlier Ubuntu versions.

---

### Post by bob brazie on 2011-05-17
Where did you find the problems others are having?

I would like to look through them too.

Thanks. Bob.

---

### Post by bob brazie on 2011-05-17
Would Unity 2d be one answer to this problem?

---

### Post by mikewhatever on 2011-05-17
I simply searched for "Radeon X1200" using the forum search field. Both Unity2d and the fallback Gnome2 should work, because they don't utilize Compiz.

---

