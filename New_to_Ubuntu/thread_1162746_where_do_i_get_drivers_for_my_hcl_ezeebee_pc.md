---
title: "where do i get drivers for my hcl ezeebee pc"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by aravindc26 on 2009-05-18
where do i get drivers for my hcl ezeebee pc ?

---

### Post by Cresho on 2009-05-18
kernel identifies drivers automatically for you but if you need specific drivers like the ones you need, you need to tell us what is happening to your device.

Be more specific.

---

### Post by aravindc26 on 2009-05-18
> **Cresho said:**
> kernel identifies drivers automatically for you but if you need specific drivers like the ones you need, you need to tell us what is happening to your device.

Be more specific.
when i clik on wine configure audio tab it shows no audio  drivers found in registry

---

### Post by Cresho on 2009-05-18
There is a test button.  see if that works in the audio tab.  Does your audio work on your pc at all?  Can you hear audio when not using wine?

just for extra measure, in the terminal, list

lspci and paste the output here

---

### Post by SunnyRabbiera on 2009-05-18
> **aravindc26 said:**
> when i clik on wine configure audio tab it shows no audio  drivers found in registry

well wine another matter, but do you get sound in wine?
Dont use wine if you are wanting to get drivers for your machine, its very hit and miss.

---

### Post by aravindc26 on 2009-05-18
> **Cresho said:**
> There is a test button.  see if that works in the audio tab.  Does your audio work on your pc at all?  Can you hear audio when not using wine?

just for extra measure, in the terminal, list

lspci and paste the output here
yeah........
i can hear audio......
but i dont understand this part of ur reply

"just for extra measure, in the terminal, list

lspci and paste the output here"

---

### Post by Cresho on 2009-05-18
in anycase, try using emulation in audio of the wine app instead of the hardware.  click apply and use the test button to see if audio works.

---

### Post by aravindc26 on 2009-05-18
> **Cresho said:**
> There is a test button.  see if that works in the audio tab.  Does your audio work on your pc at all?  Can you hear audio when not using wine?

just for extra measure, in the terminal, list

lspci and paste the output here

is this what u looking for 

```
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

```

---

### Post by Cresho on 2009-05-18
> **Cresho said:**
> in anycase, try using emulation in audio of the wine app instead of the hardware.  click apply and use the test button to see if audio works.

try this route.  realtek is an onboard audio so this might be causing issues.  There are some configurations you may need to do to get your audio working but try what i mentioned.  Your audio is fine.  It's just getting wine to work.

---

### Post by aravindc26 on 2009-05-18
> **Cresho said:**
> try this route.  realtek is an onboard audio so this might be causing issues.  There are some configurations you may need to do to get your audio working but try what i mentioned.  Your audio is fine.  It's just getting wine to work.
fyn.....then.........
where do i get graphic drivers

---

### Post by Cresho on 2009-05-18
go into system->adminstration->hardware drivers

---

### Post by aravindc26 on 2009-05-19
it says no hardware drivers found

---

