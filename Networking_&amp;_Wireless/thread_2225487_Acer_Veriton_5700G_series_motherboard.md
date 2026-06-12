---
title: "Acer Veriton 5700G series motherboard"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by kazica on 2014-05-21
Hi there I'm currently struggling trying to get Ubuntu to recognise the inbuilt network part of the motherboard for this pc. When I type in the "ifconfig" command I get the following back:```
lo    Link encap:Local Loopback
      inet addr:127.0.0.1 mask:255.0.0.0
      inet addr:  ::1/128 Scope:Host
      UP LOOPBACK RUNNING     MTU:65536  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
      TX packets:0 errors:0 dropped:0  overruns:0 carrier:0
      collisions:0 txqueuelen:0 
      RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
```Any one got any fixes for this? Thanks in advance :)

---

### Post by kazica on 2014-05-21
Sorry for the messy text I have no idea how to edit it to look like it would on the terminal

---

### Post by mörgæs on 2014-05-21
Use code tags, available in the advanced editor.

---

### Post by kazica on 2014-05-21
For some reason I can't acess that..so erm...sorry

---

### Post by Elfy on 2014-05-21
You don't need to use the advanced editor to use code tags, you can do it manually

 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by kazica on 2014-05-21
Thanks for this. Still question remains. Anything I can do to fix it?

---

### Post by Vladlenin5000 on 2014-05-22
What hardware are we talking about exactly? Try in a terminal ```
lspci
``` and post back the results...

---

### Post by kazica on 2014-05-22
Here we go: 
```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)


```


hope that's some help to you. At this moment my work around has been to put a small plug and play wifi adaptor into the machine to make it well wirless free and able to conect to the internet.

---

