---
title: "Configuring 3D graphic card"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-10-17
Hello
I just have a problem configuring my 3D graphics card and my graphics card is ATI X1650SE I tried doing that using the proprietary driver but it messed up my computer and now I'm trying to follow the step from this URL "https://help.ubuntu.com/community/RadeonDriver" The problem I am facing now is using the ```
lspci
``` command to find the hardware address of the graphics card, this is the result I got.
```
mosaab@mosaab-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
00:0a.0 Communication controller: Agere Systems Device 0620
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)
02:00.1 Display controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Secondary)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```
[SIZE="5"]**Does any one know what is the hardware address of the graphics card**[/SIZE]

---

### Post by sandyd on 2009-10-17
```

**02:00.0** VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)
**02:00.1** Display controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Secondary)

```

---

### Post by mosaabJ on 2009-10-17
> **carlee said:**
> ```

**02:00.0** VGA compatible controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Primary)
**02:00.1** Display controller: ATI Technologies Inc RV516 XT Radeon X1600 Series (Secondary)

```

Thank you carlee for your quick reply

---

