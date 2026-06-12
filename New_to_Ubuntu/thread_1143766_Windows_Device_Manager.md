---
title: "Windows Device Manager"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by hubriz on 2009-04-30
I just wonder, how will I know if the device installed on my computer are properly working and recognized by Ubuntu similar to the Windows Device Manager? In Windows, if you check Device Manager in Control Panel, unrecognized device will prompt you a yellow question mark icon beside the corresponding hardware, if there's any. As long as you're connected to the net, and the CD driver is not with you, just right click and choose Update Driver and it will search its driver by itself.

I recently installed Ubuntu 9.04, dual-booted together with Windows XP in my computer. I'm having hard time to configure my modem's driver, though on the manufacturer's site, it only provides drivers for all Windows platform(DLink DFM-5621S HSFi PCI Modem). Though I am more focus on updating other hardwares on my computer(videocard, network card, etc.) soon, I hope there is similar options or wizards Ubuntu have in updating drivers automatically.

So far, I did not encounter any installation problems, and it went fine and running as I expect. I'm a Windows user for almost a decade and excited to shift completely to Ubuntu soon.

---

### Post by halitech on 2009-04-30
Chances are if everything is working then it has detected and loaded the proper modules for your hardware. the modem is probably the only thing that won't work as it is what is called a win-modem (software based modem) which traditionally don't work very well in linux. Can you open a terminal and post the results of
```
lspci
```

---

### Post by alphacrucis2 on 2009-04-30
> **hubriz said:**
> I just wonder, how will I know if the device installed on my computer are properly working and recognized by Ubuntu similar to the Windows Device Manager? In Windows, if you check Device Manager in Control Panel, unrecognized device will prompt you a yellow question mark icon beside the corresponding hardware, if there's any. As long as you're connected to the net, and the CD driver is not with you, just right click and choose Update Driver and it will search its driver by itself.

I recently installed Ubuntu 9.04, dual-booted together with Windows XP in my computer. I'm having hard time to configure my modem's driver, though on the manufacturer's site, it only provides drivers for all Windows platform(DLink DFM-5621S HSFi PCI Modem). Though I am more focus on updating other hardwares on my computer(videocard, network card, etc.) soon, I hope there is similar options or wizards Ubuntu have in updating drivers automatically.

So far, I did not encounter any installation problems, and it went fine and running as I expect. I'm a Windows user for almost a decade and excited to shift completely to Ubuntu soon.

There is a program called gnome-device-manager which you can install from the synaptic package manager under System Administration. Once installed you will find it in Applications System tools. It is somewhat similar to the Windows device manager. I can't help with your modem query.

---

### Post by alphacrucis2 on 2009-04-30
If the device is a Winmodem as the other poster suggested then that could be tricky. There is some info here:

[http://linmodems.org/]("http://linmodems.org/")

---

### Post by hubriz on 2009-05-01
> **halitech said:**
> Chances are if everything is working then it has detected and loaded the proper modules for your hardware. the modem is probably the only thing that won't work as it is what is called a win-modem (software based modem) which traditionally don't work very well in linux. Can you open a terminal and post the results of
```
lspci
```

Here are the results..

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0b.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200]

---

### Post by halitech on 2009-05-01
definately software modem

[color="red"]00:0b.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)[/color]

Check the linmodem site that alphacrucis2 posted. If it is possible, they should know

---

