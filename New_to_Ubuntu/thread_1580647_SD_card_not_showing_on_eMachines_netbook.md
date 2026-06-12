---
title: "SD card not showing on eMachines netbook"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by kallekn on 2010-09-23
I am running Ubuntu 10.04 on an eMachines 350 netbook. Everything seems to be working fine, except that nothing happens when I put in a card in the SD card reader. Can't see the card in the file browser either. Do I need to do something else, in addition to just placing the SD card in the reader?

---

### Post by jtarin on 2010-09-23
Run the command ```
lspci 
``` in a terminal and post the output.

---

### Post by macem29 on 2010-09-23
my Acer netbook will not mount from the SD slot unless card is present on boot

---

### Post by kallekn on 2010-09-24
Here is the output:

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by jtarin on 2010-09-24
Is your card in the machine when you ran the command? If yes...then run the command ```
lsusb
```again...your card should be in.

---

### Post by kallekn on 2010-09-24
Here is the output:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 0cf2:6250 ENE Technology, Inc. 
Bus 001 Device 002: ID 0402:7675 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Yes, card was in both times.

---

### Post by jtarin on 2010-09-24
Type of card,Mfg and model?

---

### Post by kallekn on 2010-09-24
The card says SanDisk Ultra 15Mb/s SD C4 2GB.

What is Mfg?

---

### Post by jtarin on 2010-09-24
> **kallekn said:**
> The card says SanDisk Ultra 15Mb/s SD C4 2GB.

What is Mfg?Manufacturer

---

### Post by kallekn on 2010-09-24
Ok. Should I try with another card?

---

### Post by jtarin on 2010-09-24
With the card inserted, enter the command ```
fdisk -l
``` in a terminal and post the output.

---

### Post by kallekn on 2010-09-24
There is no response whatsoever to that command.

&#1042;&#1099; &#1085;&#1072; &#1089;&#1072;&#1084;&#1086;&#1084; &#1076;&#1077;&#1083;&#1077; &#1074;&#1086; &#1042;&#1083;&#1072;&#1076;&#1080;&#1078;&#1086;&#1089;&#1090;&#1086;&#1082;&#1077;? &#1040; &#1103; - &#1085;&#1072; &#1102;&#1075;&#1077; &#1064;&#1074;&#1077;&#1094;&#1080;&#1080;. :-)

---

### Post by jtarin on 2010-09-24
> **kallekn said:**
> There is no response whatsoever to that command.

&#1042;&#1099; &#1085;&#1072; &#1089;&#1072;&#1084;&#1086;&#1084; &#1076;&#1077;&#1083;&#1077; &#1074;&#1086; &#1042;&#1083;&#1072;&#1076;&#1080;&#1078;&#1086;&#1089;&#1090;&#1086;&#1082;&#1077;? &#1040; &#1103; - &#1085;&#1072; &#1102;&#1075;&#1077; &#1064;&#1074;&#1077;&#1094;&#1080;&#1080;. :-)

Try ```
sudo fdisk -l
```

Var i Sverige?

---

### Post by kallekn on 2010-09-25
kallekn@kalle-portebla:~$ sudo fdisk -l
[sudo] password for kallekn: 

Levy /dev/sda: 160.0 Gt, 160041885696 tavua
255 päätä, 63 sektoria/ura, 19457 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Levyn tunniste: 0x0002c172

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/sda1   *           1       19088   153315328   83  Linux
/dev/sda2           19088       19458     2972673    5  Laajennettu
/dev/sda5           19088       19458     2972672   82  Linux-sivutus / Solaris
kallekn@kalle-portebla:~$ 

Sorry, system in Finnish.

[http://maps.google.com/maps?f=q&source=s_q&hl=fi&geocode=&q=Skyttelinjen+55,+Lund,+Sverige&sll=37.230328,-95.712891&sspn=21.558494,56.513672&ie=UTF8&hq=&hnear=Skyttelinjen+55,+Lund,+Sk%C3%A5ne+L%C3%A4n,+Ruotsi&t=h&z=15](http://maps.google.com/maps?f=q&source=s_q&hl=fi&geocode=&q=Skyttelinjen+55,+Lund,+Sverige&sll=37.230328,-95.712891&sspn=21.558494,56.513672&ie=UTF8&hq=&hnear=Skyttelinjen+55,+Lund,+Sk%C3%A5ne+L%C3%A4n,+Ruotsi&t=h&z=15)

---

### Post by jtarin on 2010-09-25
OK...your card does not show in fdisk so it is not being detected.

---

### Post by jtarin on 2010-09-25
> **kallekn said:**
> Ok. Should I try with another card?
If you have ....try with those previous commands to see if it is detected.

I live in Vladivostok but I'm not Russian...American teaching English.

---

### Post by kallekn on 2010-09-25
OK, I'll give it a try with another card. Somebody else in this thread mentioned booting the machine with SD card in place, can that make any difference? A bit cumbersome if you have to think of that each time booting the computer, anyway.

[www.kniivila.net](www.kniivila.net)

---

### Post by jtarin on 2010-09-25
> **kallekn said:**
> OK, I'll give it a try with another card. Somebody else in this thread mentioned booting the machine with SD card in place, can that make any difference? A bit cumbersome if you have to think of that each time booting the computer, anyway.

[www.kniivila.net](www.kniivila.net)While cumbersome....give it a shot and if it does,maybe we can get some info that will allow you to set it up differently.

---

### Post by kallekn on 2010-09-25
No luck. Booted with SD card in place, no difference whatsoever as far as I can see. I'll try to find another card, but this is looking really bleak. :-(
(Was going to write "real", but then remembered you are an English teacher...)


kallekn@kalle-portebla:~$ sudo fdisk -l
[sudo] password for kallekn: 

Levy /dev/sda: 160.0 Gt, 160041885696 tavua
255 päätä, 63 sektoria/ura, 19457 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Levyn tunniste: 0x0002c172

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/sda1   *           1       19088   153315328   83  Linux
/dev/sda2           19088       19458     2972673    5  Laajennettu
/dev/sda5           19088       19458     2972672   82  Linux-sivutus / Solaris
kallekn@kalle-portebla:~$

---

### Post by QLee on 2010-09-26
At least for the last couple of years, I think those eMachines are built by Acer and thus may share some of the characteristics of Acer netbooks. I remember seeing posts in the forum about troubles with SD cards on Acer netbooks. You might want to look through those to see if anything applies.

---

### Post by kallekn on 2010-09-26
Yes, I think my eMachine is made by Acer. Was there any solution to the problem in those threads?

At least I can access the same SD card by inserting it into a card reader, and connecting the card reader to one of the USB ports. So no problem with the card. But it would be nice to be able to insert it directly into the machine.

---

### Post by avacado on 2010-10-14
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)

many acer aspire one have the same ENE technology card reader
There is no linux driver as yet
lf you try lsusb then device ocf2:6250 is the correect bug to watch
otherwise buy an external linux card reader or just use your camera like an external drive.

---

### Post by kallekn on 2010-10-14
Ok thanks. Only I have no idea what the bug thing means - is there a solution coming?

I am having problems using a card reader as well, the card shows up but as read only.

---

### Post by avacado on 2010-10-14
Welcome I have an acer aspire one d260 with the same card reader

we are brothers in the way of card reader desperation.

please subscribe to my bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)

It may take some time for a volunteer developer to write a driver for this card reader and you can add weight to the issue.

In the mean time may I suggest buying an external linux compat card reader or use your camera as an external drive. I had to wait about 12 months before somebody wrote the driver for my ricoh card reader in the other rig,,, patience, and subscribe to my bug.

---

### Post by Mal de Mer on 2010-10-15
I'm also having these problems with 10.04 on the em350.
I get the same results for lspci & lsusb.

Here is the System Log - Messages output when twice inserting & removing the following SD cards:
SanDisk ExtremeIII ESP 2GB
EagleTek SDHC Class6 16GB
Toshiba Class 4 2GB.

Oct 16 11:17:20 laptop kernel: [  355.624172] usb 1-5: new high speed USB device using ehci_hcd and address 5
Oct 16 11:17:20 laptop kernel: [  355.758029] usb 1-5: configuration #1 chosen from 1 choice
Oct 16 11:19:35 laptop kernel: [  490.884589] usb 1-5: USB disconnect, address 5
Oct 16 11:19:44 laptop kernel: [  499.656162] usb 1-5: new high speed USB device using ehci_hcd and address 6
Oct 16 11:19:44 laptop kernel: [  499.791038] usb 1-5: configuration #1 chosen from 1 choice
Oct 16 11:19:54 laptop kernel: [  509.730448] usb 1-5: USB disconnect, address 6
Oct 16 11:20:08 laptop kernel: [  524.180158] usb 1-5: new high speed USB device using ehci_hcd and address 7
Oct 16 11:20:09 laptop kernel: [  524.314145] usb 1-5: configuration #1 chosen from 1 choice
Oct 16 11:20:15 laptop kernel: [  530.542847] usb 1-5: USB disconnect, address 7
Oct 16 11:20:25 laptop kernel: [  540.736164] usb 1-5: new high speed USB device using ehci_hcd and address 8
Oct 16 11:20:25 laptop kernel: [  540.870975] usb 1-5: configuration #1 chosen from 1 choice
Oct 16 11:20:31 laptop kernel: [  547.003120] usb 1-5: USB disconnect, address 8
Oct 16 11:21:11 laptop kernel: [  586.656149] usb 1-5: new high speed USB device using ehci_hcd and address 9
Oct 16 11:21:11 laptop kernel: [  586.790002] usb 1-5: configuration #1 chosen from 1 choice
Oct 16 11:21:24 laptop kernel: [  599.694080] usb 1-5: USB disconnect, address 9
Oct 16 11:21:34 laptop kernel: [  609.584160] usb 1-5: new high speed USB device using ehci_hcd and address 10
Oct 16 11:21:34 laptop kernel: [  609.717791] usb 1-5: configuration #1 chosen from 1 choice
Oct 16 11:21:41 laptop kernel: [  616.944979] usb 1-5: USB disconnect, address 10

Does this info help, are there any suggestions?

I'm having no probs with my EEEPC900,
but my wife wants to use an EM350.....

---

### Post by Mal de Mer on 2010-10-15
Sorry everybody,
I made a NOOB mistake & didn't see the three pages of this thread,
I only read the first.

I'll follow the bug's progress with interest.

Thanks for everyone's input.

---

