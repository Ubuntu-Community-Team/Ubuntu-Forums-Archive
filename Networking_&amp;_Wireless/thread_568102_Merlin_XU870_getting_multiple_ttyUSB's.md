---
title: "Merlin XU870 getting multiple ttyUSB's"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by Alex1200GS on 2007-10-05
Hi all,

I'm trying to install a Merlin Novatel XU870 PCI-Express card on my Sony Vaio SZ1XP/C running Ubuntu 7.04 Feisty Fawn and I could really use some help with it.

The instructions provided by the manufacturer are here: [http://www.novatelwireless.com/support/merlin-xu870-linux.html](http://www.novatelwireless.com/support/merlin-xu870-linux.html)
They seemed pretty straight-forward, so I rolled my sleeves up. However, as soon as I connect the card to the slot, the output I get from /var/log/messages is this: 

```
Oct  5 18:13:48 vaio kernel: [ 6320.336000] usb 2-2: new full speed USB device using uhci_hcd and address 4
Oct  5 18:13:48 vaio kernel: [ 6320.500000] usb 2-2: configuration #1 chosen from 1 choice
Oct  5 18:13:48 vaio kernel: [ 6320.504000] airprime 2-2:1.0: airprime converter detected
Oct  5 18:13:48 vaio kernel: [ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB0
Oct  5 18:13:48 vaio kernel: [ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB1
Oct  5 18:13:48 vaio kernel: [ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB2
Oct  5 18:13:48 vaio kernel: [ 6320.504000] airprime 2-2:1.1: airprime converter detected
Oct  5 18:13:48 vaio kernel: [ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB3
Oct  5 18:13:48 vaio kernel: [ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB4
Oct  5 18:13:48 vaio kernel: [ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB5

```

dmesg|tail outputs this:

```
[ 6320.336000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[ 6320.500000] usb 2-2: configuration #1 chosen from 1 choice
[ 6320.504000] airprime 2-2:1.0: airprime converter detected
[ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB0
[ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB1
[ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB2
[ 6320.504000] airprime 2-2:1.1: airprime converter detected
[ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB3
[ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB4
[ 6320.504000] usb 2-2: airprime converter now attached to ttyUSB5

```

Trying to cat ttyUSB0 through 5 returns nothing; it just sits there for ever, waiting for me to Control+C it off.

When I pull the device off the slot, the /var/log/messages output is:

```
Oct  5 18:33:28 vaio kernel: [ 7500.948000] usb 2-2: USB disconnect, address 4
Oct  5 18:33:28 vaio kernel: [ 7500.948000] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
Oct  5 18:33:28 vaio kernel: [ 7500.948000] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
Oct  5 18:33:28 vaio kernel: [ 7500.952000] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
Oct  5 18:33:28 vaio kernel: [ 7500.952000] airprime 2-2:1.0: device disconnected
Oct  5 18:33:28 vaio kernel: [ 7500.952000] airprime ttyUSB3: airprime converter now disconnected from ttyUSB3
Oct  5 18:33:28 vaio kernel: [ 7500.956000] airprime ttyUSB4: airprime converter now disconnected from ttyUSB4
Oct  5 18:33:28 vaio kernel: [ 7500.956000] airprime ttyUSB5: airprime converter now disconnected from ttyUSB5
Oct  5 18:33:28 vaio kernel: [ 7500.956000] airprime 2-2:1.1: device disconnected

```

and dmesg|tail is:

```
[ 7500.948000] usb 2-2: USB disconnect, address 4
[ 7500.948000] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
[ 7500.948000] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
[ 7500.952000] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
[ 7500.952000] airprime 2-2:1.0: device disconnected
[ 7500.952000] airprime ttyUSB3: airprime converter now disconnected from ttyUSB3
[ 7500.956000] airprime ttyUSB4: airprime converter now disconnected from ttyUSB4
[ 7500.956000] airprime ttyUSB5: airprime converter now disconnected from ttyUSB5
[ 7500.956000] airprime 2-2:1.1: device disconnected

```

BTW, I get the same thing when I try to connect my Palm Treo 750 (the phone runs through the available USB ports and then disappears).

I tried to google the known universe about it but I'm not getting any relevant results so I'm stuck here. Any hint to put me on the right track would be highly appreciated.

Alex

---

### Post by Alex1200GS on 2007-10-05
Also, lsusb returns this:

```
Bus 005 Device 003: ID 05ca:1830 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  

```

no matter if the card is inserted or not.

---

### Post by WiWi on 2007-11-21
Hi Alex,

got it working under Ubuntu 7.10. You might check my personal blog for a detailed description:

[http://www.sw83.de/blog/2007/11/21/howto-get-your-3g-card-xu870-working-under-ubuntu-710-gutsy-gibbon/]("http://www.sw83.de/blog/2007/11/21/howto-get-your-3g-card-xu870-working-under-ubuntu-710-gutsy-gibbon/")

Good luck :)

---

### Post by giumbolo on 2008-06-12
It's a pity that your blog is not online. Why don't you paste here, the way you did?

---

