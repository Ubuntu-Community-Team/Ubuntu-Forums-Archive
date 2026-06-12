---
title: "PDA connection"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by DiGiTGOD on 2008-09-04
I'm trying to get my PDA phone connected to Linux to transfer some files over to it...

I'm not bothered about syncing it with anything... all I want to do is be able to transfer files over....

I've followed the tutorial on the synce website... but when I connect the phone and run the command "synce-pls" I get the following error...

martin@FRED:/etc/init.d$ synce-pls
synce-pls: symbol lookup error: synce-pls: undefined symbol: rapi_connection_from_name

The device seems to be connecting properly as you'll see from the dmesg output below... but I can't seem to get around this problem...

[376730.628630] usb 1-2: new full speed USB device using ohci_hcd and address 36
[376730.852713] usb 1-2: configuration #1 chosen from 1 choice
[376732.680269] rndis0: register 'rndis_host' at usb-0000:00:02.0-2, RNDIS device (SynCE patched), 00:00:00:00:00:00

Anyone got any ideas??

Any help appreciated...

Martin

---

### Post by Eric B on 2008-09-20
I believe that the issue is the MAC RNDIS device (SynCE patched), 00:00:00:00:00:00. I am having problems as well and trying to find a solution.

---

### Post by zingalala on 2009-09-11
Has anyone found a solution on how to resolve "RNDIS device, 00:00:00:00:00:00" problem?

I just want to use "Internet Connection Sharing" (ICS) from Windows Mobile 6.1 based smartphone with Ubuntu. I am using Ubuntu 9.04, Kernel 2.6.28-15.

---

