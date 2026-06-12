---
title: "Screen Resolution"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by jimsbluegras7 on 2009-12-29
Hi All! 

I am green green green with Linux. The resolution on my screen yesterday was fine and editable. I turned the computer OFF. Overnight and when I turned it back on today it was set to low resolution and when I opened Screen Resolution it would not allow me to change anything. Yesterday I could change it just fine. Any suggestions? Here is what I have.

jim777@jim777-desktop:~$ sudo lshw -C video
[sudo] password for jim777: 
  *-display               
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: driver=prosavage_smbus latency=32 maxlatency=255 mingnt=4 module=i2c_prosavage
jim777@jim777-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Communication controller: Conexant HCF 56k Data/Fax/Voice Modem (Worldwide) (rev 08)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
jim777@jim777-desktop:~$ 
jim777@jim777-desktop:~$

---

### Post by s.fox on 2009-12-29
Hello,

Can you clarify what you mean by:

> **jimsbluegras7 said:**
> I opened Screen Resolution it would not allow me to change anything.

What exactly happens?   [Here]("http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html") is a guide that might be of some use to you.

Please post back,

Silver Fox

---

