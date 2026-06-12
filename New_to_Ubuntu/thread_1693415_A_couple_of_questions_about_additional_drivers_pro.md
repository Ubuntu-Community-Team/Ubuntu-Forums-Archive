---
title: "A couple of questions about additional drivers program"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-02-22
When I go there it just says "no proprietary drivers on this system" and nothing is listed under it, I would expect there would be some drivers listed. So am I correct in saying that it doesn't list the drivers that are being used by your system.(if it doesn't is there some program that does)? I'm getting a new video card that ubuntu suggest using linux drivers with. So how does these drivers that are needed get in the additional drivers program?

---

### Post by mikewhatever on 2011-02-22
When the system detects a piece of hardware that has a proprietary driver for it, you'll get a popup notification that the driver is available. It's not for listing drivers.

---

### Post by Jon Anderson on 2011-02-23
> **mikewhatever said:**
> When the system detects a piece of hardware that has a proprietary driver for it, you'll get a popup notification that the driver is available. It's not for listing drivers.
Thank you, do you have a thought on a program that shows the drivers that are in the system. Is there a such thing

---

### Post by tajiknomi on 2011-02-23
> **Jon Anderson said:**
> Thank you, do you have a thought on a program that shows the drivers that are in the system. Is there a such thing

You can get the driver info by the given Commands:-

E.G for sound & video...

```
sudo lshw -C display | grep driver

sudo lshw -C sound | grep driver
```

---

### Post by mastablasta on 2011-02-23
also drivers in linux are usually part of the kernel (core). a newer kernel will probably have newer drivers ;-)

---

### Post by Jon Anderson on 2011-02-23
> **tajiknomi said:**
> You can get the driver info by the given Commands:-

E.G for sound & video...

```
sudo lshw -C display | grep driver

sudo lshw -C sound | grep driver
```
  The line to put in terminal for sound gives me the driver numbers but it won't work for my video drivers and that is the one I need ,my computer freezes and I'm looking for a solution

---

### Post by mastablasta on 2011-02-24
what video card do you have? post the output of
 
lspci
 
command that will list you devices.

---

### Post by tajiknomi on 2011-02-24
> **Jon Anderson said:**
> The line to put in terminal for sound gives me the driver numbers but it won't work for my video drivers and that is the one I need ,my computer freezes and I'm looking for a solution

As mastablasta Suggested, what Gfx Card you have...?

Moreover ,Their is an Option "**Additional-Drivers**" OR "**Hardware-Drivers**" in System>Administration.

---

### Post by Jon Anderson on 2011-02-24
[QUOTE=mastablasta;10489365]what video card do you have? post the output of
 
lspci
 
command that will list you devices.[/QUOTE

I have the VIA/s3g unichrome pro video card and I want to see if the right drivers are installed ,it freezes solid have to rehard boot.

jbander@ubuntujon:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
jbander@ubuntujon:~$

---

### Post by cariboo on 2011-02-24
Unfortunately S3/Unichrome have the worst linux support possible. To see if you are using the unichrome driver, open a terminal and type:

```
sudo lshw -C display
```

look for the word driver in the output.

---

### Post by Jon Anderson on 2011-02-24
> **cariboo907 said:**
> Unfortunately S3/Unichrome have the worst linux support possible. To see if you are using the unichrome driver, open a terminal and type:

```
sudo lshw -C display
```look for the word driver in the output.

*-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2
       resources: memory:e8000000-ebffffff memory:ec000000-ecffffff memory:ed000000-ed00ffff
I don't see the driver listed

---

