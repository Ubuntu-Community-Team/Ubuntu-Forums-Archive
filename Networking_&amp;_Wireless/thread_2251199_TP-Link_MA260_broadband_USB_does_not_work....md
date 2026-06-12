---
title: "TP-Link MA260 broadband USB does not work..."
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by geppetto on 2014-11-02
I've seen many posts for this device, but none of the recipes I've tried helps me.

When I connect the device, most times the broadband connection does not show up in the "radar", in the up/right corner of the screen. I need to unplug/plug the device several times in order to have it displayed, and in this case it works fine.

As expected, when it does not work there is a "2357:f000" device in lsusb:

```

$ lsusb | grep 2357
Bus 003 Device 019: ID 2357:f000

```

When it works the product Id is different:

```

$ lsusb | grep 2357
Bus 003 Device 021: ID 2357:9000

```

Apparently I get more chances to get the device working when there is an SD inserted, but I cannot be sure about this.

I have tried the modeswitch spells, but none works:
```

sudo usb_modeswitch -v 0x2357 -p 0xf000 -P 0x9000 -M "5553424312345678000000000000061b000000020000000000000000000000"

```
or
```

sudo usb_modeswitch -v 2357 -p f000 -V 2357 -P 9000 -W -I -n -M '5553424312345678000000000000061e000000000000000000000000000000' -2 '5553424312345678000000000000061b000000020000000000000000000000'

```
and also simply
```

sudo usb_modeswitch -v 2357 -p f000 -R

```

Any help?

---

