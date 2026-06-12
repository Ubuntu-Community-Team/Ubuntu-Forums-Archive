---
title: "ACPI errors"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Caletara on 2010-01-01
In trying to get my webcam/skype to work, I checked dmesg and got this lovely repeating error. I'm currently running Karmic. 

[526427.508614] ACPI Exception: AE_LIMIT, Returned by Handler for [SystemIO] 20090521 evregion-424
[526427.508626] ACPI Error (psparse-0537): Method parse/execution failed [\_GPE._L09] (Node f700edb0), AE_LIMIT
[526427.508690] ACPI Exception: AE_LIMIT, while evaluating GPE method [_L09] 20090521 evgpe-568
[526535.565273] ACPI Error: Illegal I/O port address/length above 64K: 0x00400020/4 20090521 hwvalid-154

I am however at a loss on how to fix it. Thank you for any help!

---

### Post by AndThenWhat on 2010-01-01
Sounds like this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/475704](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/475704)

Might not have anything to do with your webcam.

---

### Post by Caletara on 2010-01-01
Thanks so much!

---

### Post by starsprout on 2010-01-21
I'm seeing the same ACPI Error here. My system freezes up virtually every time it goes to screensaver.

Is there a fix for this?

---

### Post by dcottingham on 2010-01-24
I also have the endless ACPI messages.  There appears to be no fix. Wouldn't hurt to wander over to launchpad and click the metoo button. Might encourage those who know how to debug it that it's worth doing.

---

### Post by sti11_learning on 2010-05-08
I too ran into this bug. I was able to stop it by adding ```
acpi=off
``` to grub.cfg. However, this made my onboard NIC stop working correctly. As a result, I reverted it and still have the ACPI messages.

---

