---
title: "Wireless patches not working"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by aj25bd10 on 2008-06-18
I am a new user and I hope this is in the correct place but I have seen other very similar topics here. I had Gutsy Gibbon for a month or so before I upgraded yesterday to Hardy Heron. My wireless required a patch in Gutsy but the same patch is not working for me in Hardy. I have been through many step by step tutorials but to no avail. When I checked my Hardware Drivers, my graphics card appears there but the wireless does not. Before I attempted to fix it with the step by step tutorials, it would display that the wireless card was in use but not enabled. I would of course click to enable it and I was to to restart the computer for it to take effect. I would restart but nothing would have changed. Like I said before, however, the wireless card is no longer visible when I look at the Hardware Drivers. Help me if you can. Thanks!

---

### Post by Ayuthia on 2008-06-18
Can you post your lspci -nn?  It will help us know what wireless card you are using.  Thanks and welcome to the community!

---

### Post by aj25bd10 on 2008-06-18
lbobby@bobby-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 81)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
02:01.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
02:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
02:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
02:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
02:04.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

Hope that helps? Thanks.

---

### Post by aj25bd10 on 2008-06-18
bump

---

### Post by rhlobo on 2008-06-19
There are some users experiencing some wireless problems when connecting thrue WAP after 06-17 ubuntu updates. The list of disponible networks works correctly but the connection process just hangs and wont connect.

If you think this is your problem, I will be checking [https://answers.launchpad.net/ubuntu/+question/36575](https://answers.launchpad.net/ubuntu/+question/36575) constantly.

Best regards

---

### Post by Corrupt3d on 2008-06-19
> **aj25bd10 said:**
> I am a new user and I hope this is in the correct place but I have seen other very similar topics here. I had Gutsy Gibbon for a month or so before I upgraded yesterday to Hardy Heron. My wireless required a patch in Gutsy but the same patch is not working for me in Hardy. I have been through many step by step tutorials but to no avail. When I checked my Hardware Drivers, my graphics card appears there but the wireless does not. Before I attempted to fix it with the step by step tutorials, it would display that the wireless card was in use but not enabled. I would of course click to enable it and I was to to restart the computer for it to take effect. I would restart but nothing would have changed. Like I said before, however, the wireless card is no longer visible when I look at the Hardware Drivers. Help me if you can. Thanks!

Hi, 
I had pretty much the same thing happen to me and my Broadcom card.
After messing around and removing a few packages, my Card no longer showed up in the 'Hardware Drivers'

The solution is this:

Applications > Accessories > Terminal
 
(copy and paste the green stuff in)
$ [COLOR="Green"]sudo aptitude install b43-fwcutter[/COLOR] [COLOR="Red"]# for Broadcom cards
[/COLOR]
After it installs you will need to [COLOR="Red"]Restart your computer[/COLOR].
Once you log in, it should up, simply click it to activate it (in my case I didn't even have to click it).
Enter your wifii info and enjoy your wireless.

---

