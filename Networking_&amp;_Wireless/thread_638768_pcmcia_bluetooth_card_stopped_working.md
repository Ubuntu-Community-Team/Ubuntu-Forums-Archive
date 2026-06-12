---
title: "pcmcia bluetooth card stopped working"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by flowKub on 2007-12-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/174993](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/174993) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				conceptronic bluetooth pcmcia used to work fine under kubuntu edgy, feisty and initially gutsy. now all of a sudden it's not working any more and makes kbluetooth crash.

On inserting the card, /var/log/messages reads:

Dec 9 00:42:12 flo-acer-kub kernel: [ 2208.724000] pccard: PCMCIA card inserted into slot 0
Dec 9 00:42:12 flo-acer-kub kernel: [ 2208.724000] pcmcia: registering new device pcmcia0.0
Dec 9 00:42:12 flo-acer-kub kernel: [ 2208.772000] ttyS0: detected caps 00000700 should be 00000100
Dec 9 00:42:12 flo-acer-kub kernel: [ 2208.772000] 0.0: ttyS0 at I/O 0x400 (irq = 3) is a 16C950/954
Dec 9 00:42:22 flo-acer-kub hciattach: BCSP initialization timed out

root@flo-acer-kub:~# lspcmcia
Socket 0 Bridge: [yenta_cardbus] (bus ID: 0000:02:06.0)
Socket 0 Device 0: [serial_cs] (bus ID: 0.0

Strangely, the card came back to action when I deinstalled obexpush, but only until the next reboot...

---

