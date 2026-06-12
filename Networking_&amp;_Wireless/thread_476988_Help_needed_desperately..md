---
title: "Help needed desperately."
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by kcspcmn on 2007-06-17
I'm stumbling through the process of getting my laptop internet-ready with Ubuntu. I have installed ndiswrapper and ndiswrappergtk from the installation CD. I have the driver that I believe goes to my 2wire 802.11g wireless adapter card. I installed the driver, and now the computer can successfully tell me if the card is plugged in or not. When I go to configure a network, all I see are wired and modem, no wireless. From here, I am completely stuck. No lights on my card, no idea where to go to continue.

---

### Post by empthollow on 2007-06-17
to see if the system is seeing the card type```
ifconfig -a
``` in a terminal.  If it is not seeing the card there is an issue with ndiswrapper.

---

### Post by dmizer on 2007-06-18
before ifconfig -a ... i think it's extremely important to know what card you have.

please post the output of:
```
lspci
```

also, it's important to know if ndiswrapper even has the driver installed correctly for your card:
```
ndiswrapper -l
```

---

### Post by scannerdarkly on 2007-06-18
Question, is this Feisty that you are running?

---

### Post by kcspcmn on 2007-06-18
I am running feisty, yes.


casey@ubuntu:~$ ndiswrapper -l
wlanuig : driver installed
        device (1260:3886) present
----------------------------------------------------------------
casey@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:D0:4B:B1:2E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xe300 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
----------------------------------------------------------------
casey@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P/KN266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
02:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

---

### Post by empthollow on 2007-06-18
you could check this thread out, this person has your same card
[http://ubuntuforums.org/archive/index.php/t-30445.html](http://ubuntuforums.org/archive/index.php/t-30445.html)

---

