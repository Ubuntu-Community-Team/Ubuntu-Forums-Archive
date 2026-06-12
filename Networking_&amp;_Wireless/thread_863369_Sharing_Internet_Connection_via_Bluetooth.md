---
title: "Sharing Internet Connection via Bluetooth?"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by pwaldo on 2008-07-18
Hi all,

I just got a fancy new Dell Precision M6300 laptop that has Bluetooth, and I want to play! 

I have a Windows desktop machine that is connected to the Internet and also has Bluetooth.  I want to get to the Internet from the laptop via Bluetooth.  Unfortunately, I have no clue as to how to set this up in **KDE**.

I know Bluetooth is working, as I can use my BT Mouse.  "sudo pand --search" returns immediately with no ouput and I have no bnep device.

I'm running Kubuntu Hardy 64-bit.

Thanks in advance!

---

### Post by fwendt on 2008-08-04
If you had Linux on both computers it would work like this:

computer A (with the internet access):
Start 'pand -s --role NAP' and make sure it runs ok (ps aux | grep pand).
Lookup the MAC address of the bluetooth interface (hciconfig hci0 | grep Address | cut -d ' ' -f 3).

computer B:
Start 'pand -c MA:C_:FR:OM:AB:OV --service NAP -z'.

You will now have a network interface (bnep0) on both computers. Add ip addresses to them and enabled SNAT or MASQ.

I have no clue to if there's a KDE-way to do this via some GUI. Good luck.

---

