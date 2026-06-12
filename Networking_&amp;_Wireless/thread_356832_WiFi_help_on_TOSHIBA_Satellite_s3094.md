---
title: "WiFi help on TOSHIBA Satellite s3094"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by djvic87 on 2007-02-08
Hi im totally new on ubuntu, I finished installing ubuntu with the help of kebes of this forum.
My main problem is that I dont know what to do first to get wireless connection, since my laptop has wifi built in.

Also, since many people have bragged about a program called network manager, which I think helps people find a wireless connection, I tried installing it and it tells me a message saying that it cannot be installed on my computer type i386, and it said either the application requires special software or the vendor decided to not support my computer type.

Can someone please help? Thanks.

---

### Post by Floppyjoe on 2007-02-08
I don't know if I can help you with the Network manager problem but maybe you can get your wireless working if it does not already work? What is your wireless card? Open a terminal and enter:

```
lspci
```

Please post the output here.

---

### Post by djvic87 on 2007-02-08
How do I do that? Once again, im totally new to this.

---

### Post by Floppyjoe on 2007-02-08
Click on Applications/Accessories/Terminal then enter the command:
```
lspci
```
The command basically means list PCI devices.

---

### Post by djvic87 on 2007-02-09
When i do that on the laptop, i cant seem to paste it on openoffice because when i try to save it even as a doc format, it gives me errors saying "error saving document Untitled1: /media/sda1/manny2.doc
What is going on?

---

### Post by Floppyjoe on 2007-02-09
Do you have a direct cable connection to the network with the laptop?

---

### Post by djvic87 on 2007-02-09
No, why? on my other computer it does, the one im using now. Should i connect the cable to my laptop? (which connects to a wireless modem router)

---

### Post by Floppyjoe on 2007-02-09
If you can connect(the laptop) through the cable we can try some stuff out like find out your wireless cards identification to see if it works with Linux.

---

### Post by djvic87 on 2007-02-09
Well ok, it is now connected to my laptop. The internet is kind of slow on my laptop, here is the code.

manny@manny-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8136 (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
04:06.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
04:06.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
04:06.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
04:06.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
04:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
manny@manny-laptop:~$

---

### Post by Floppyjoe on 2007-02-09
This is your wireless card here:
> Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Can you post the output of the command:
```
iwconfig
```

---

### Post by k0rv3n on 2007-02-11
Hi.

I have the same problem but with a Toshiba Satellite P100-208.
It seams to be the same wireless card in my laptop and the output I get from iwconfig is:

```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:25   Missed beacon:0


```

So I guess that eth1 is the wireless connection.
How do I setup a connection to my access point?

---

### Post by paddyS on 2007-02-15
With the same laptop and a fresh install of Dapper

I did manage to get a connection to wireless straight out the box but I can't get access at work because they use WPA not WEP which doesn't seem to be supported by any of the apps.  I couldn't get the wireless manager to install at first as I needed to have the Nvidia driver installed ???? Go figure on that one! but now that's there it works fine.

Not sure how I can help more but I just set it to use ida1 as default and it connected!

Paddy

---

