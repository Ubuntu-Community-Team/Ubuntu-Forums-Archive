---
title: "Default boot drive priority (defaults to external drive)"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by WileyGaia on 2009-05-12
Hi. I have an external hard drive connected via USB. Each time I turn on my PC, the BIOS attempts to boot from the external drive, and fails as I only have music and pics on the external drive. I can solve the problem by rebooting and going into BIOS and changing the boot disk priority to the IDE drive. However, next time I turn off and on again, the priority has changed back to external drive, and I then need to go back into BIOS etc...
How can I keep my IDE drive at the top of the list i.e. always get my machine to boot from my IDE drive? 
[Ver 8.10]

---

### Post by Jon Monreal on 2009-05-12
> **WileyGaia said:**
> Hi. I have an external hard drive connected via USB. Each time I turn on my PC, the BIOS attempts to boot from the external drive, and fails as I only have music and pics on the external drive. I can solve the problem by rebooting and going into BIOS and changing the boot disk priority to the IDE drive. However, next time I turn off and on again, the priority has changed back to external drive, and I then need to go back into BIOS etc...
How can I keep my IDE drive at the top of the list i.e. always get my machine to boot from my IDE drive? 
[Ver 8.10]

Do you know what the motherboard and BIOS are? This should not happen, so long as you actually move the IDE drive to the top of the boot order and save this order.

More information could help me help you fix this problem.

Thanks,
-Jon

---

### Post by WileyGaia on 2009-05-13
Hi not sure how to get that info, but after scratching around on the "System" menu, I think this is what you are after:
Intel Dual E2200
BIOS e-820
PS: yes each time i move the IDE to the top of the list and save, after which it boots fine (but only for that boot -next time around the boot fails and IDE is back fown at number 2 after the USB drive). I am currently getting around this by unplugging the external drive each time I boot...
I am alos considering the 9.04 upgrade which might resolve this?

---

### Post by lazyart on 2009-05-13
This is not an issue with Ubuntu, as it is your motherboard that is deciding what device to boot from.

Try disabling boot from USB altogether.

Curious, are you going to the boot menu or into Setup?  Boot menu would only give you boot options for one time use.  Setup would let you configure a bunch of other things, as well as default boot order.

---

