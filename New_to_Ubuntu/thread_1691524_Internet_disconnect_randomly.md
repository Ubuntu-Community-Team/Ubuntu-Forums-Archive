---
title: "Internet disconnect randomly"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by robro on 2011-02-20
Hello all,
I have googled a bit, searched in the forum but i cant find anything that helps,
At random times my internet automatically disconnects,
It didn't do this in windows.

I have finally found a good bandwidth monitor so at least i can keep track of my bandwidth when it does disconnect,

Thanks for your help, if you need any more info please tell me :)

---

### Post by spikoley on 2011-02-20
Are you using ethernet or wireless?  If you are using wireless then what type of wireless card is it?  Use the command below to find out the model number.

```
lspci
```

---

### Post by suomalainen on 2011-02-20
I had this problem with my wireless GSM broadband carrier.

I then configured GNOME PPP Dialup Tool using a hard lock onto GPRS. Problem went away.

However, you need to search for the right/correct code based on your usb stick manufacturer. This can mean lot's of searching.

Sorry can't help further.

---

### Post by robro on 2011-02-20
its a verizon usb760 modem, result of lspci:
```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)


```

---

### Post by spikoley on 2011-02-20
Try searching the forum for [USB760]("http://ubuntuforums.org/search.php?searchid=79539882").  It looks like other were able to resolve issues with it.

---

### Post by robro on 2011-02-20
> **spikoley said:**
> Try searching the forum for [USB760]("http://ubuntuforums.org/search.php?searchid=79539882").  It looks like other were able to resolve issues with it.

Thanks, i didn't find out how to fix the problem, but i know what is wrong, apparently the timeout on network manager is turned on :|

---

### Post by whatthefunk on 2011-02-20
You could ditch network manager for Wicd...

---

### Post by robro on 2011-02-20
And i would in a heartbeat if i could get the thing to work

---

### Post by robro on 2011-02-21
bump

---

### Post by spikoley on 2011-02-21
Please provide us with more details about the current issue.  It will help us help you.

---

### Post by robro on 2011-02-22
ok, At random times my internet automatically disconnects and it doesn't let me connect unless i pull out the modem and plug it back in, if you need any more information just ask :)

---

