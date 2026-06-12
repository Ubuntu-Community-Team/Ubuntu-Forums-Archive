---
title: "Intel 3954ABG versus Hardy - drops connection"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by mykrob on 2008-08-31
Just bought a new laptop, a Gateway M-6881. THe wifi chipset is an Intel 3954ABG. It works out of the box, however, it drops the connection after a few minutes. Network Manager still shows it connected, but it cannot ping, pull a page, or anything.

What do i need to do to get this wifi working?

Thanks,
-myk

---

### Post by mykrob on 2008-08-31
here's more detailed information on the wifi chipset:

```

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:95:05:76
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network

```

---

### Post by mykrob on 2008-08-31
Just tried installing openSuse 11, i get the same results with it too.. From what i understand, this chipset used to work. WOnder how or why it got broken..

Anyway, if you guys can help, please speak up. Otherwise, i'm stuck with Vista for a bit :)

---

### Post by mykrob on 2008-09-01
I am dual booting with Vista. Someone in another forum suggested shutting the laptop down completely for a minute or two and cold booting to LInux. He suggested that WIndows may not be completely releasing the device from a restart versus a shutdown. Gonna reinstall Kubuntu and try again.

In the meantime, still awaiting any help you can provide.

Thanks,
-myk

---

### Post by mykrob on 2008-09-02
d@mmit.. I am now using a Belkin F5D7050 usb wifi adapter... it works flawlessly so far, just plug and play..

However, I would love to get the internal wifi sorted out. It seems that the issue may be power related. I left the laptop plugged into AC for two hours with music streaming. It was still going when I got back home. I unplugged it, and within five minutes, the connection dropped again.

here's some more dmesg info:

[http://pastebin.ca/1191745](http://pastebin.ca/1191745)

---

### Post by mykrob on 2008-09-02
..just keeping it where i can see it.. These pages get filled up quick.

---

### Post by mykrob on 2008-09-03
bump

---

### Post by mykrob on 2008-09-07
anybody at all....

---

### Post by ALainONE on 2008-09-07
Try this thread... [here]("http://ubuntuforums.org/showthread.php?t=911763&highlight=3945")

Hope it helps!

---

### Post by mykrob on 2008-09-29
still no luck.

just want to see if anyone else can help with this

---

### Post by mykrob on 2008-09-30
i tried adding a newer firmware and also tried another suggestion, something about a module option about hardware scan, still the same issue no matter what i do!

---

### Post by bravebear on 2008-10-07
Had same thing happening on my Toshiba Satellite R25, same card. 

I installed [wicd]("http://wicd.sourceforge.net/") wireless network manager, which automatically uninstalled some other packages. Some how it fixed the dropped connection so far.
Weird.
Call it Voodoobuntu!

---

