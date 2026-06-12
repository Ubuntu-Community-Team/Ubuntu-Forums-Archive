---
title: "Intel PRO Wireless Not Detected"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by gobbluth on 2006-08-23
Hello, and thanks in advance to anyone who is able to help.

I had NetworkManager installed and working with my wireless network before I updated to xserver *.3, and then after downgrading and upgrading to *.4 it no longer recognizes my wireless card. The NetworkManager icon shows a red "NO" sign over an image of a cable and when I click on it, it says "No network devices have been found."

My laptop uses an Intel PRO/Wireless 2200 BG
Here is my lspci output:

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV41.8 [GeForce Go 6800] (rev a2)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:03:01.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
0000:03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)

And my ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:12:3F:D1:07:9D
          inet addr:70.179.71.187  Bcast:70.179.79.255  Mask:255.255.240.0
          inet6 addr: fe80::212:3fff:fed1:79d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2131291 (2.0 MiB)  TX bytes:245345 (239.5 KiB)
          Interrupt:209

eth1      Link encap:Ethernet  HWaddr 00:12:F0:74:52:A1
          inet addr:70.179.73.88  Bcast:70.179.73.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xe000 Memory:dcffd000-dcffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

I believe that eth1 is the wireless interface. Thank you again in advance!

---

### Post by gobbluth on 2006-08-24
bump

I tried the workaround in [this thread]("http://ubuntuforums.org/showthread.php?t=232349") but no such luck. I tried that because I noticed my wireless LED was also not lighting up. Gah, what to do.

---

### Post by gobbluth on 2006-08-24
Alright, I just fixed this myself based on advice from another thread. All I had to do was comment out my wireless interface in the /etc/network/interfaces file and NetworkManager immediately picked up on it when I rebooted. Can anyone explain to me why this is, I'm just curious. Also, NM did not pick up on it until I used the standard keyboard shortcut for turning on/off my wireless card (Fn+F2), but nothing on the screen or my keyboard (i.e. the wi-fi LED) showed a distinction between my wireless card being on or off. Is there some way I can check which way it is currently switched for future troubleshooting?

Thanks!

---

### Post by SimonJW on 2006-08-24
I don't know why your /etc/network/interfaces file was changed, but I know that NetworkManager ignores cards in this file in order to stop it interfering with other programs, configurations, and cards that the user may not want settings changed for.

Also, as far as I know, the key-combination for turning on/off the card is a hardware thing, and therefore that Wifi LED is the only way of knowing. You might be able to tell using Ubuntu though. Try testing the output of these commands when the card is on and off, and see if there are any differences you could use to test:
```

iwconfig
modinfo ipw2200
ifconfig
iwlist wlan0 scan
```

---

### Post by arkepp on 2006-09-14
The LED is actually activated by software, which does not exist under Linux afaik.

To see whether the card is active or not, open a terminal and run "iwconfig".

If you see "Tx-Power=20 dBm" the card is active, otherwise you'll see "Tx-Power=off"

---

### Post by sid78669 on 2008-05-31
Hi, I am new to Ubuntu, I just switched to it from Windows as i have taken up a course in Programming and now have a reason to switch:lolflag:. Anyways, i dnt know how to comment so could you please tell me how in details so i might do it too???

thanx alot

---

