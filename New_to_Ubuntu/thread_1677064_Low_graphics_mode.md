---
title: "Low graphics mode"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by linuxnewbei on 2011-01-28
Hello,

[INDENT]After leaving Ubuntu idle for more than 10 minutes, Ubuntu itself went into low graphics mode. Then I again logged in and all the compizconfig effects were disabled. There was an error that said unable to enable desktop effects.
[/INDENT]
How do I find which graphics card and which video driver is there on my computer? If there is no graphics card, then which graphics card do I need? 

Please help,
LinuxNewbei.

---

### Post by mastablasta on 2011-01-28
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
and you can post your ouput in this thread, so we can see what we're dealing here :-)

---

### Post by linuxnewbei on 2011-01-28
Thanks for replying. This is the output when I type the command "lspci":

> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


---

### Post by mastablasta on 2011-01-29
you are using 
> Intel Corporation 82945G/GZ Integrated Graphics Controller

which means the graphics is an chip on your motherboard. these don't tend to be good, especially older intel ones. you could check the hardware drivers (in the system menu) if any drivers are available for your chip. intel chips have soem issues with linux especially older ones.

if however you have some money on your hands a dedicated graphics card would give much much better performance (nVidia or ATI/AMD). they cost about 30-40 EUR upwards...

---

