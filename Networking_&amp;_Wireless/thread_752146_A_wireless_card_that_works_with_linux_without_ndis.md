---
title: "A wireless card that works with linux without ndiswrapper?"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by DigitalDuality on 2008-04-11
anyone know of a wireless card, relatively cheap, that works with linux without ndiswrapper.

I just bought a D-Link DWL-510  and no matter what windows driver i use i can't seem to make it work.  So i figure if i'm buying another one, i might as well make sure 100% there's someone out there that can verify it works without ndiswrapper.

---

### Post by Junglizer on 2008-04-11
Can't give you any specific models (well not one's that are probably in your price range) but you'll have the best luck with Atheros chipped cards. Try to snag one with an 'AR5212' or 'AR5213' chipset listing. These are from the Atheros 5004 family group, and most of them work amazingly well with the Madwifi drivers. I have a Belkin Wireless G card, pretty standard, nothing fancy that works well, but different versions always seem to have different chipsets.

---

### Post by raymac46 on 2008-04-11
Look here:
[http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)
DWL-G520 is Atheros based and works well. That's what I use. WDA-1320 and 2320 are also good.

---

### Post by dstew on 2008-04-11
Check this support document: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

It includes community experience with different cards with different distributions. There is not really a guarantee of trouble-free use, because there are so many possible combinations of hardware, meaning card + motherboard systems. I personally have an Atheros-based card that works fine with the native drivers, in Feisty.

---

### Post by bobdob20 on 2008-04-11
> **DigitalDuality said:**
> I just bought a D-Link DWL-510 and no matter what windows driver i use i can't seem to make it work.

I have a D-Link DWL-510 and it worked out of the box with ubuntu. Madwifi and Ndiswrapper are supposed to only support rev. B, but the box says mine is rev. C and it still works.

---

### Post by brian_p on 2008-04-11
> **DigitalDuality said:**
> anyone know of a wireless card, relatively cheap, that works with linux without ndiswrapper.

I just bought a D-Link DWL-510  and no matter what windows driver i use i can't seem to make it work.  So i figure if i'm buying another one, i might as well make sure 100% there's someone out there that can verify it works without ndiswrapper.

I've used cards with Atheros and Ralink chipsets with success. I'm be tempted to buy one of the ones written about at

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=7241](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=7241)

---

### Post by Princey on 2008-04-11
My D-Link DWL 510 worked out of the box flawlessly. You don't need ndiswrapper to get it to work. Just make sure that the linux-restricted-modules are installed.

---

### Post by DigitalDuality on 2008-04-11
^
Well in that case i'll give it another shot.  Much appreciated for all the responses.

---

### Post by DigitalDuality on 2008-04-11
> **Princey said:**
> My D-Link DWL 510 worked out of the box flawlessly. You don't need ndiswrapper to get it to work. Just make sure that the linux-restricted-modules are installed.

hmm i just installed ubuntu (after trying mthbuntu and opensuse 10.3, and fedora 8)  and nonew of them recognize it out of the box.

---

### Post by Princey on 2008-04-12
Do you know what revision whether it's A, B, C, D or E that you're using? What does the command > lspci -v | less yield when typed in the terminal? That should help us help you better.

---

### Post by heyho on 2008-04-12
Some more info:

[https://www.fsf.org/resources/hw/net/wireless/cards.html](https://www.fsf.org/resources/hw/net/wireless/cards.html)

---

### Post by mathenge on 2008-04-12
I have a D-Link WNA-1330 and it works flawlessly. Nothing to do.

---

### Post by DigitalDuality on 2008-04-13
> **Princey said:**
> Do you know what revision whether it's A, B, C, D or E that you're using? What does the command  yield when typed in the terminal? That should help us help you better.

00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9012
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ec000000-edffffff
        Prefetchable memory behind bridge: e0000000-e7ffffff
        Capabilities: <access denied>

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9012
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at d000 [size=256]
        Memory at ef000000 (32-bit, non-prefetchable) [size=256]

---

### Post by Princey on 2008-04-13
From what you post here, there's no mention of you wireless card. Are you sure that's all the command yielded? You're using a pci card, it should show.

---

### Post by DigitalDuality on 2008-04-13
> **Princey said:**
> From what you post here, there's no mention of you wireless card. Are you sure that's all the command yielded? You're using a pci card, it should show.

that's all it yielded.  it's like the system (no matter the OS other than windows) will not recognize the card is even plugged in.

---

### Post by Princey on 2008-04-13
Can you list me your system specs? Like what make/model of computer, memory etc? I find that funny that lspci would yield so short a list. Something isn't right here unless you're using a computer where everything is onboard save your ethernet card which is the only one listed in your output besides your chipset.

---

