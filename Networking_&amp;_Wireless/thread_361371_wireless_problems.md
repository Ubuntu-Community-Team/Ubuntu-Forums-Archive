---
title: "wireless problems"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by raaah on 2007-02-14
Hi, I'm using ndiswrapper and rt61.inf for my F5D7000.

ndiswrapper -l:

rt61 : driver installed
           device (bla bla) present (alternate driver: rt61pci)
           device (bla) present (alternate driver: rt61pci)

when i run "sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper" I'm greeted by the following:

ioctl[SIOCSIWMODE]: Device or resource busy
Could not configure driver to use managed mode

Trying to associate with ... (SSID='BeBox' freq=2462 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.

Those last 3 lines repeat indefinitely. I've been using many guides and none seem to work. Any suggestions?

I cannot download anything or use apt-get since even my ethernet isn't working, though i do have internet access through windows xp...

---

### Post by corax on 2007-02-14
Hi !

Are you sure that the interface is wlan0 ?

Is it working if you switch WPA off ? (I know it is insecure ... just for testing)

And anyway what chip does the card have ? Are you sure Ndiswrapper is necessary ?

As I see here there are three versions of this card with different chips ! 

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

The first versions of this card works with bcmw15a.inf (and NOT with rt61.inf that also can be a problem) and ndsiwrapper.
The second (atheros chip) is working with madwifi driver and well supported in linux (i can confirm that since i have the same chip on a netgear card).
The third is ralink is working out of the box too.

So please type ```
lspci
``` to the terminal and post the output.

good luck :)

---

