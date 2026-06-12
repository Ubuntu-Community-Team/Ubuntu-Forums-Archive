---
title: "tiny laptop"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by jabie5 on 2007-05-09
i have a tiny laptop with built in wireless. i started up Ubuntu 7.04 desktop live cd, but cannot connect to the internet.

i have read through posts to find an answer, i opened terminal window and typed lspci to find out what wireless device i have this is wot i got

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
00:09.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
00:0a.0 Network controller: Agere Systems Unknown device ab34
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
ubuntu@ubuntu:~$ 

but what do i do now

thanks
johnny

---

### Post by jabie5 on 2007-05-10
come guys give a newbie a hand to get his wireless connection going

---

### Post by p4|\|d0r4 on 2007-05-12
I have exactly the same laptop ....
I struggled with the built-in wireless card. Without writing a driver yourself,  there doesn't seem to be any way to use ab34 natively under linux. However, it does work if you use ndiswrapper to load the windoze driver.

---

### Post by jabie5 on 2007-06-18
ive looked into that but couldnt figure out how to use it any help would be great. also are there any good tutorials for begginers, i like too read as much as i can before asking newbie questions

thanks 
johnny

---

