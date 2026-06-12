---
title: "Anyone have a Novatel Merlin XU870 (Dell Expresscard 5510) working?"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by bimmerd00d on 2007-04-25
I just picked one up and it says it supports linux 2.6 kernel on the Dell website.  I followed the guide on novatel's site, but it's not working.  It fails when i try to connect.  Something about "invalid syntax ' ' " in hsdpa_chatoptions.  Any of you guys have some time to help me fix this?  I'm still getting used to running linux fulltime on my laptop.  Oh, Dell Inspiron E1705 is what i'm working with.

[http://www.novatelwireless.com/support/merlin-xu870-linux.html](http://www.novatelwireless.com/support/merlin-xu870-linux.html)

---

### Post by bimmerd00d on 2007-04-26
Here's tail -f /var/log/messages

Apr 26 09:44:53 bhlaptop -- MARK --
Apr 26 10:04:54 bhlaptop -- MARK --
Apr 26 10:13:53 bhlaptop kernel: [ 5357.484000] usb 1-1.3: new full speed USB device using ehci_hcd and address 4
Apr 26 10:13:54 bhlaptop kernel: [ 5357.576000] usb 1-1.3: configuration #1 chosen from 1 choice


and Here is dmesg

[   26.152000] [fglrx] max single Inv  = 0
[   26.152000] [fglrx] total      TIM  = 0
[   26.160000] Bluetooth: Core ver 2.11
[   26.160000] NET: Registered protocol family 31
[   26.160000] Bluetooth: HCI device and connection manager initialized
[   26.160000] Bluetooth: HCI socket layer initialized
[   26.172000] Bluetooth: L2CAP ver 2.8
[   26.172000] Bluetooth: L2CAP socket layer initialized
[   26.388000] Bluetooth: RFCOMM socket layer initialized
[   26.388000] Bluetooth: RFCOMM TTY layer initialized
[   26.388000] Bluetooth: RFCOMM ver 1.8
[   26.480000] NET: Registered protocol family 17
[ 5357.484000] usb 1-1.3: new full speed USB device using ehci_hcd and address 4
[ 5357.576000] usb 1-1.3: configuration #1 chosen from 1 choice
bimmerd00d@bhlaptop:~$

---

### Post by bimmerd00d on 2007-04-26
Scratch that, got it working :guitar: 

I'll post a howto thread in a bit.

---

