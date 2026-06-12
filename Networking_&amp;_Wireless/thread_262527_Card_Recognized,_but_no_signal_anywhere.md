---
title: "Card Recognized, but no signal anywhere"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by kohlerbn on 2006-09-21
My wireless card is recognized by UBUNTU however, it has no signal everywhere that I go with it. I have a Intel Pro/Wireless 2915. I have installed Network Manager and it doesn't pick anything up either. 

LSPCI says this

0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)

and IWCONFIG says this 

lo        no wireless extensions.
eth0      no wireless extensions.
eth1      radio off  ESSID:off/any
Mode:Managed  Channel:0  Access Point: Not-Associated
Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
Retry limit:7   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sit0      no wireless extensions.


I have tried everything I can think of, and many howTo's. Can anyone help me?

---

### Post by wieman01 on 2006-09-22
Can you run:
> iwconfig eth1 scan
If there is no output (and you definitely turn on your router... silly tought I guess), then I am afraid **Windows** has turned of your wireless device **("eth1 radio off")**. The resolve this problem you need to boot Windows and enable the wireless adapter, then restart and boot Ubuntu.

The latter is a common & known problem. After that you should be able to find your network.

---

### Post by kohlerbn on 2006-09-22
I am not running a dual boot. Is there a way to enable the wireless card in UBUNTU?

---

### Post by wieman01 on 2006-09-22
Do you happen to have a radio/wireless button somewhere on the keyboard or right in front of the monitor? Is this a laptop computer?

---

### Post by civetta on 2006-10-01
Yup,

I've got the same problem. Only I upgraded from Breezy to Dapper and now to Edgy beta. My lspci used to list my wireless card as intel 2200 b/g (and wireless worked). Now it's correctly listed as intel 2915 abg byt wireless no longer works. I can turn the radio switch on and off from my keyboard and iwconfig recognizes this (either "no wireless extension" when off, or an output similar to the one you got when on):

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can't figure out why I'm not able to detect any networks.

---

