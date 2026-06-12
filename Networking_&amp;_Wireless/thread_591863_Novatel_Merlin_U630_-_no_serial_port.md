---
title: "Novatel Merlin U630 - no serial port"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by inunda on 2007-10-25
Hi all.
Can't put my card to work cause it doesn't assign a serial port like it should.
I insert the card, the blue light starts blinking but no serial port assigned.
Tried other linux distros and it worked but not on ubuntu :'(
Please help.

Dmesg:
[ 2976.596000] pccard: card ejected from slot 0
[ 4000.804000] pccard: PCMCIA card inserted into slot 0
[ 4000.804000] pcmcia: registering new device pcmcia0.0
[ 4000.804000] pcmcia: request for exclusive IRQ could not be fulfilled.
[ 4000.804000] pcmcia: the driver needs updating to supported shared IRQ lines.
[ 4000.844000] pcmcia: registering new device pcmcia0.1
[ 4000.844000] pcmcia: request for exclusive IRQ could not be fulfilled.
[ 4000.844000] pcmcia: the driver needs updating to supported shared IRQ lines.

lspcmcia:
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:06:04.0)
Socket 0 Device 0:      [serial_cs]             (bus ID: 0.0)
Socket 0 Device 1:      [serial_cs]             (bus ID: 0.1)

pccardctl:
Socket 0:
  product info: "Novatel Wireless", "Merlin UMTS Modem", "U630", ""
  manfid: 0x00a4, 0x0276
  function: 2 (serial)

---

### Post by mj0g on 2007-12-13
Hmm, I'm trying to get this card working and got the same dmesg output. Did you have any luck getting it going in the end?

Thanks,
/Mike

---

### Post by inunda on 2007-12-14
Not a clue :-(

---

