---
title: "Audio card supplanted by Modem"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by pteri498 on 2008-12-04
I installed a modem in my computer for faxing, and now my sound doesn't work. The card that normally is controlled with the Volume Control isn't there, and instead it shows my modem, which doesn't have an audio-out, anyway.

My lspci shows the following;

```

$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:04.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:04.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:04.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

I believe the third item from the top, the Intel Audio Driver, is what I want, but I don't know how to enable it.

Any ideas?

Thanks.

---

### Post by pteri498 on 2008-12-04
badda bing badda bump

---

