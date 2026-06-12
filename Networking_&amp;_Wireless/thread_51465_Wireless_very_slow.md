---
title: "Wireless very slow"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by joevandyk on 2005-07-24
Hi,

My PCI 802.11g wireless connection is very slow.  I can download at about 7KB/s.  I have another really really old laptop, like close to 9 years old i think running ubuntu right here and I can download at about 400KB/s on it.

I don't remember the download speed being that bad in Windows with this card.  It's an Airlink AWLH3025.

lcpci: 
0000:02:06.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

dmesg grepping for "acx":
```

joe@big:~$ dmesg | grep -i acx
acx100: It looks like you've been coaxed into buying a wireless network card
acx100: that uses the mysterious ACX100/ACX111 chip from Texas Instruments.
acx100: You should better have bought e.g. a PRISM(R) chipset based card,
acx100: since that would mean REAL vendor Linux support.
acx100: Given this info, it's evident that this driver is quite EXPERIMENTAL,
acx100: thus your mileage may vary. Visit http://acx100.sf.net for support.
acx100: Warning: compiled to use 16bit I/O access only (compatibility mode). Set Makefile ACX_IO_WIDTH=32 to use slightly problematic 32bit mode.
acx_init_module: dev_info is: TI acx_pci
acx_init_module: TI acx_pci.o: Ver 0.2.0pre8 Driver initialized, waiting for cards to probe...
acx_probe_pci: WARNING: ACX111 support is quite experimental!
Found ACX111-based wireless network card at 0000:02:06.0, irq:16, phymem1:0xfc020000, phymem2:0xfc000000, mem1:0xffffff0000044000, mem1_size:8192, mem2:0xffffff00003c0000, mem2_size:131072
acx_select_io_register_set: using ACX111 io resource addresses (size: 56)
acx_probe_pci: TI acx_pci: Using IRQ 16
acx_reset_mac: enable soft reset...
acx_reset_mac: disable soft reset and go to init mode...
Trying to load firmware: '/lib/hotplug/firmware/TIACX111.BIN-2.6.10-5-amd64-generic'
acx_write_fw: Firmware written.
acx_write_fw (firmware): 0, acx_validate_fw: 0
acx_reset_dev: boot up eCPU and wait for complete...
acx_reset_dev: Received signal that card is ready to be configured :) (the eCPU has woken up)
acx_reset_dev: Clean up cmd mailbox access area
acx100: allocated net device wlan0, driver compiled against wireless extensions v17 and Linux 2.6.10-5-amd64-generic
************* acx_init_mac_1 *************
acx111_init_packet_templates: Init max packet templates
acx111_create_dma_regions: set up acx111 queue memory configuration (queue configs + descriptors)
acx100: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05. Uploaded firmware 'Rev 0.1.0.11' (0x03010101).
creating /proc entry driver/acx_wlan0
creating /proc entry driver/acx_wlan0_diag
creating /proc entry driver/acx_wlan0_eeprom
creating /proc entry driver/acx_wlan0_phy

```

And there's more stuff, but when I try to paste all of it, this board complains about there being too many smilies and/or images in the post.  I just noticed that first blurb about it being experimental, that's not good!  :-)  I bet that's where my problem lies.  Anyone know of anything I should do, or should I just get another better supported wireless card?  And in that case, recommendations?

Thanks,
Joe

---

### Post by joevandyk on 2005-07-24
I'm currently trying out the steps at [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

Hopefully it will work better afterwards.  It's weird, because the card works fine, it's just hella slow.  And I noticed that it stops working after two days or so.. need to reboot the machine to get it to respond.

---

### Post by joevandyk on 2005-07-24
And I'm running with an AMD 64 3000+ cpu in 64 bit ubuntu, btw.

---

### Post by joevandyk on 2005-07-24
The new drivers didn't seem to help any.  Still very very slow.  :(

---

### Post by joevandyk on 2005-07-24
I also tried the ndiswrapper, but it complained about the non-64 bit Windows drivers.  ARGH.

So, I guess I need to get a new card?  Which one is good?

---

