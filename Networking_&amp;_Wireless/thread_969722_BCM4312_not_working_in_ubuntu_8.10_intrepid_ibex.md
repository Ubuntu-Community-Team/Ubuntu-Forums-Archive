---
title: "BCM4312 not working in ubuntu 8.10 intrepid ibex"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by vance morris on 2008-11-03
This is a Dell Latitude 910 (Mini 9)
release : Ubuntu 8.10 Intrepid Ibex
uname -r : 2.6.27-7-generic
relevant lspci output :
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
 Subsystem: Broadcom Corporation Device [14e4:04b5]
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Interrupt: pin A routed to IRQ 17
 Region 0: Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: wl
 Kernel modules: wl

I have installed the b43-fwcutter package and extracted the firmware for this BCM4312 wifi adapter but when I load up jockey there is only the proprietary broadcom STA driver showing as an option. According to linuxwireless.org, this card is supported by the b43 drivers.

I have manually removed the wl module and installed the b43 module, but this doesn't result in any functional interfaces appearing under ifconfig or under the NetworkManager applet.

Thanks in advance for any help.

---

### Post by Ayuthia on 2008-11-03
Actually, this card is not supported by the linuxwireless.org group.  The card was known as the 4310 card and was updated in 8.04.1 and is now known as the 4312 card.  The wl driver and ndiswrapper are the only options for this card at this time.

---

### Post by vance morris on 2008-11-03
Thanks for the info.
I don't suppose you have a lead on if linuxwireless.org will be supporting this card in the near future?

---

### Post by Ayuthia on 2008-11-03
> **vance morris said:**
> Thanks for the info.
I don't suppose you have a lead on if linuxwireless.org will be supporting this card in the near future?

The b43 mailing list has not said too much about it lately.  If I recall correctly, they were finishing up on the reverse engineering on it so it looks like it will still be a while.

---

### Post by vance morris on 2008-11-03
Okay, I've got a BCM4311 card from a few years ago.  Without knowing any specifics, you think there's a good chance it will work with b43?

---

### Post by Ayuthia on 2008-11-03
> **vance morris said:**
> Okay, I've got a BCM4311 card from a few years ago.  Without knowing any specifics, you think there's a good chance it will work with b43?

The 4311 cards should work with the b43 driver.  I have a 4311 rev 01 card and it works really well with the b43 driver.  I have not seen how well the 4311 rev 02 cards work though.

---

### Post by spikenick on 2008-11-04
I have the 4311 chipset. If I have a fresh install of Intrepid Ibex Ubuntu 8.10 how would I go about using the b43 driver.

---

### Post by Mr Green on 2008-11-04
Just use 8.04, it works there. Why bother with using 8.10. Doesn't add any value over 8.04 anyway.

---

### Post by Ayuthia on 2008-11-04
> **spikenick said:**
> I have the 4311 chipset. If I have a fresh install of Intrepid Ibex Ubuntu 8.10 how would I go about using the b43 driver.

The 4311 card has two options--the Broadcom STA (wl) driver and the open source b43 driver.  If you would like to use the b43 driver go to System->Administration->Hardware Drivers and activate the b43 driver and make sure that the Broadcom STA driver is disabled.  You will need an internet connection in Ubuntu to get this to work because the b43 driver needs an additional firmware file to be downloaded to make it work.  Once it is complete, you will want to blacklist the wl driver:
```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by vance morris on 2008-11-06
I dug out an old laptop and pulled the bcm4311 card out of it.  Placed it in my new laptop and was able to select the B43 driver in the hardware manager.

This still did not fix my problem entirely.  NetworkManager would not detect that the new 4311 was installed and operational.  After messing around with the config for NetworkManager for 30 minutes, I gave up on it and installed wicd.

Now everything is super duper.  Thanks for the help :)

---

