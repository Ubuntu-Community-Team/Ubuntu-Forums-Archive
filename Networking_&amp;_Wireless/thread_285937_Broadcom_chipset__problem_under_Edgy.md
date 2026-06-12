---
title: "Broadcom chipset  problem under Edgy"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by xor.be on 2006-10-27
Hello all,

I bought a Sony Ericsson GC89 card a while back.
I uses a broadcom chipset. I was never able to make it work using ndiswrapper under previous version.

I was exited to see that with Edgy it was detected (altho i had this after ndiswrappering it too)

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Monitor  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The only problem seems to be the firmware, dmesg output = 

17179791.960000] pccard: CardBus card inserted into slot 0
[17179791.960000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[17179791.960000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179791.960000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179791.964000] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[17179791.964000] ACPI: PCI Interrupt 0000:03:00.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179791.964000] 0000:03:00.1: ttyS2 at I/O 0xe000 (irq = 11) is a 16550A
[17179794.600000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179794.604000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

It seems the firmware isn't available in lib/firmware, and i'm supposed to add manually or using bcm43xx-fwcutter tool, but i just can't find the firmware.

The only sollutions i can find online involve using ndiswrapper, but i feel i shouldn't do this seeing as the card is detected.

I'm soooo close :( 

Could anybody point me in the good direction please ?

With great respect, xor

---

### Post by hardhu on 2006-10-27
> **xor.be said:**
> Hello all,

It seems the firmware isn't available in lib/firmware, and i'm supposed to add manually or using bcm43xx-fwcutter tool, but i just can't find the firmware.



Could anybody point me in the good direction please ?

With great respect, xor

You should try to extract the firmware from wl_apsta.o; see this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
or go to irc channel #bcm-users in freenode network.

---

### Post by xor.be on 2006-10-27
Thx a million Hardhu, =D> 

I've been trying to make this card work since quite some time.

But, if anybody wants to use the Sony Ericsson GC89 card under Ubuntu (Edgy) the above page works fine, except you have to install the firmware from the cafuego package, otherwise he won't extract the files due to older version or smth.

Also, the scan won't be succesfull untill you sudo up the interface,and put it on 11mb. (I mention this because it didn't work when it was supposed to in the walktrough).

From this point on the iface and pre-up commandos don't seem to work under edgy, i also wasn't able to associate. I rebooted,unplugging the lan and to my surprise it worked, i got dhcp'ed.

I wouldn't know about the keys,since the networks i use only have mac filtering.

I also haven't looked into the GPRS/EDGE,but i remember them working with ndiswrapper and the original driver, except i never found how to connect to radio.:-k

---

