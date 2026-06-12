---
title: "Slow wifi perfomance with Broadcome wifi module BCM43602"
date: 2019-12-30
forum: Networking &amp; Wireless
---

### Post by sinemora on 2019-12-30
Hi everyone, this is my first post and I am fairly new to Linux and Ubuntu, so apologies for my inaccurate terminology or any mistakes I might be making.

I've successfully installed Ubuntu 18.04 on my early 2015 laptop equipped with a Broadcom BCM43602 wifi module. Overall, everything works well enough but the wifi's speed is simply abysmal, well below what I get in the non-linux systems. I've been searching for a solution for the past few days and I found out mine is a common issue, but all I could find was the suggestion of using the brcmfmac open-source drivers.

This is the result of my "lspci -vvnn | grep -A 9 Network" command in terminal:

03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43602 802.11ac Wireless LAN SoC [14e4:43ba] (rev 01)
    Subsystem: Apple Inc. BCM43602 802.11ac Wireless LAN SoC [106b:0133]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytestrie
    Interrupt: pin A routed to IRQ 71
    Region 0: Memory at c1400000 (64-bit, non-prefetchable) [size=32K]
    Region 2: Memory at c1000000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: <access denied>
    Kernel driver in use: brcmfmac

I understand the brcmfmac is loaded and fully functioning, but I don't see much of an improvement over the proprietary Broadcom drivers. I tried building and installing a broadcom-wl-dkms package I found on the Arch support page, and offered as a solution to my problem, but as I said I am not enough tech-savvy to pull that off.

Left without other options I turned to this Forum, and I would be grateful for any help with this issue.

I would be grateful if an Admin could move this post into the 'Networking' section of the forum as it seems more appropriate to the issue. My apologies for not posting it there in the first place.

---

### Post by ajgreeny on 2020-01-05
*Thread moved to **Networking & Wireless**.* which is more appropriate and a better fit.

See **Wireless-info** in my signature, download it and run the script, then report back the output here or by using [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) if the output is too large to add direct. One of our wifi experts will hopefully be able to suggest a solution.

---

