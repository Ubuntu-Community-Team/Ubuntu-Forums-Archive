---
title: "Reason: 2=PREV_AUTH_NOT_VALID"
date: 2021-06-13
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2021-06-13
I have an Intel AX200 wifi pcie card (04:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)) that didn't automatically connect.
It usually automatically connects.
I need to use the wifi for this network because I use the wired for testing a different network (they are not both connected at the same time though).

```
[   10.597071] wlp4s0: authenticate with xx:xx:xx:xx:xx:xx
[   10.599309] wlp4s0: send auth to xx:xx:xx:xx:xx:xx (try 1/3)
[   10.704712] wlp4s0: authenticated
[   10.708039] wlp4s0: associate with xx:xx:xx:xx:xx:xx (try 1/3)
[   10.745605] wlp4s0: RX AssocResp from xx:xx:xx:xx:xx:xx (capab=0x1511 status=0 aid=1)
[   10.748810] iwlwifi 0000:04:00.0: Got NSS = 4 - trimming to 2
[   10.761977] wlp4s0: associated
[   10.806532] IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready
[   11.030258] wlp4s0: Limiting TX power to 27 (30 - 3) dBm as advertised by 40:3f:8c:79:4d:1f
[   11.885682] wlp4s0: deauthenticated from xx:xx:xx:xx:xx:xx (Reason: 2=PREV_AUTH_NOT_VALID)
```

What does Reason 2 mean and can I prevent it?

Is there a way to make network manager reconnect?

---

### Post by MAFoElffen on 2021-06-14
Intel's drivers for this card went to Linux Kernel in version 5.1. What kernel are you running?

Second, this may sound strange, but people running this card and reporting the connection error you said you got... Said that their problems were resolved when they upgraded their BIOS firmware. This also resolved issues with this card preventing their systems from going into a suspend state. Something to try.

---

### Post by bjlockie on 2021-06-15
> **MAFoElffen said:**
> Intel's drivers for this card went to Linux Kernel in version 5.1. What kernel are you running?

Second, this may sound strange, but people running this card and reporting the connection error you said you got... Said that their problems were resolved when they upgraded their BIOS firmware. This also resolved issues with this card preventing their systems from going into a suspend state. Something to try.

5.11.0-18-generic

My computer's BIOS?
It is a computer from 2019,
I have a BIOS dated 2019/7/5
I can upgrade to one dated 2019/7/25
I doubt it will fix my problem.

---

### Post by MAFoElffen on 2021-06-15
Admittingly, I know nothing about Raspberry Pi's. Trying to imagine how you connect a PCIe card to a Raspberry Pi... But still...

Maybe you could add that as a TAG so someone who has done wireless on Raspberry Pi, might have some tips on anything special for them. 

Wait, let me ask my son. He has a Raspberry Pi and is using Ubuntu. LOL

---

### Post by MAFoElffen on 2021-06-15
Okay. Just got off the phone with my son... He said for a board from 2019, you probably have a Pi3 board(?)

Here's what he told me. Run Raspbian or Ubuntu Mate.

He said that the person who did the Pi Version of Ubuntu Mate did a lot of good scripting work. Especially in the area of Wireless. There were a lot of hacks that Raspbian needed to get wireless working for Pi. That person ported all those hacks into the Mate version.

He also says, to not expect for it to be very fast. The hardware is what it is. The Pi4 is notably faster, but is still is nowhere from being a Desktop in the way of performance.

* So running Lubuntu on Pi3? Known, there are hacks to make it work, and I am not sure what those were. You would have to probably visit the Raspbian boards to find out what those where. Or change to Mate...

Me? That's as far as I know for Raspberry Pi.

---

