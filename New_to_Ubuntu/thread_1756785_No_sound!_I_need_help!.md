---
title: "No sound! I need help!"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by grobar87 on 2011-05-12
Hi,
I install Lubuntu 11.04 on old PC (CPU 850Mhz,RAM 320Mb,20Gb hard disk).Everything works great except sound.Alsa is installed and Pulseaudio.This is the output of "lspci":
```
dejan@dejan-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:0c.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:10.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
dejan@dejan-desktop:~$ 

```
I need help to fix this sound problem.
Thanks and sorry for my english.

---

### Post by audiomick on 2011-05-12
Are you sure there is a sound card in there? I can't see anything in that list that I recognise as a sound card... :-k

---

### Post by grobar87 on 2011-05-13
Hardware problem.I change my sound card and now everything is ok.Thanks for help.

---

### Post by cavalier911 on 2011-05-13
The buntu's no longer have ISA pnp detection support in the kernel.ISA kernel module drivers are included but require you to identify the correct module and add it to /etc/modules to auto load.
Pnpdump identifies the vendor and device id of ISA PNP devices in addition to io , irq, and dma info.
Download/Install isapnptools:
```
 [SIZE="1"]wget http://old-releases.ubuntu.com/ubuntu/pool/universe/i/isapnptools/isapnptools_1.26-5_i386.deb[/SIZE]

```
```
sudo dpkg -i isapnptools_1.26-5_i386.deb
```
```
pnpdump > pnpdump.txt
```
```
leafpad pnpdump.txt
```

---

