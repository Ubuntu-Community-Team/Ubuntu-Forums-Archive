---
title: "hp card reader driver"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by monoiz15 on 2009-03-16
hey i have an hp pavilion dv5 1002nr with intrepid... i was trying to find a way to get the card reader working because a found an old point and shoot camera with an XD card and im used to SD but the reader still works.. i was just wondering if anyone could point me in the right direction an far as getting a driver or whatever cuz that wud b pretty cool.. 
thanks in advance! :)

---

### Post by Gannon8 on 2009-03-16
There should already be one installed. Try plugging it in and see if gnome/whatever your display manager is mounts it (or look for devices in /dev). If that doesn't work, try doing some apt-cache's to look for drivers.

---

### Post by acreech on 2009-03-16
> **monoiz15 said:**
> hey i have an hp pavilion dv5 1002nr with intrepid... i was trying to find a way to get the card reader working because a found an old point and shoot camera with an XD card and im used to SD but the reader still works.. i was just wondering if anyone could point me in the right direction an far as getting a driver or whatever cuz that wud b pretty cool.. 
thanks in advance! :)

The internal readers for the xD cards are not suppurted by linux. I believe that it is because the drivers for the reader have not been made open source. So to use your xD card you will need an external reader.

---

### Post by Gannon8 on 2009-03-16
Ah, thats right. Its a printer.

Yeah, I haven't much luck with printer card readers. You will probably need an external reader.

---

### Post by monoiz15 on 2009-03-16
ok thanks guys.. yea i was pretty sure id put an sd card in there before that worked but i guess xd doesnt.. well i think my gf said she had an external reader.. THANKS!!

---

### Post by dserodio on 2009-04-18
I have a DV5-1160BR and the card reader doesn't work for SD cards either... Do I have to load some module or something like that?

---

### Post by cariboo on 2009-04-18
Are you sure it doesn't work, or is it not  autoounting the device. Open a Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n10
```

after you plug the memory card in, and paste the output in your next post. This will tell us whether the SD card is detected or not.

Jim

---

### Post by dserodio on 2009-04-20
Here's the output from dmesg after inserting a SD card
```
[  119.641757] wlan0: associate with AP 00:14:bf:b4:a1:1c
[  119.645636] wlan0: RX AssocResp from 00:14:bf:b4:a1:1c (capab=0x411 status=0 aid=2)
[  119.645636] wlan0: associated
[  120.839149] /dev/vmnet: open called by PID 3690 (vmnet-bridge)
[  120.839221] /dev/vmnet: hub 2 does not exist, allocating memory.
[  120.839305] /dev/vmnet: port on hub 2 successfully opened
[  120.839374] bridge-wlan0: is a Wireless Adapter
[  120.839402] bridge-wlan0: up
[  120.839425] bridge-wlan0: attached
[  135.772525] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
```

---

