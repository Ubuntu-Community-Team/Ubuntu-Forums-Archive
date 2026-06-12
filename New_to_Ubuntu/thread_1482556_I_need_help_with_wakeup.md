---
title: "I need help with wakeup"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Nidwow on 2010-05-13
With:

```
echo > USB3 /proc/acpi/wakeup
``````

USB3      S4     enabled   pci:0000:00:13.0

```But it went back to disabled after reboot, is there a way I can make it ENABLED every time after boot up?

Thanks,

---

### Post by -humanaut- on 2010-05-13
You might be able to do with KMS instead of echo > try enable_etc_etc or SET

---

### Post by Nidwow on 2010-05-13
> **-humanaut- said:**
> You might be able to do with KMS instead of echo > try enable_etc_etc or SET

Thank you for the reply.  The truth is this does not help me - new to linux.

how do I type it in exactly?

SET > USB3 /proc/acpi/wakeup ?

I can resume suspend and hibernate by pressing the power switch but it get to be a real pain as my pc is under the desk and the power switch is behind the door.  

Thanks,

---

### Post by -humanaut- on 2010-05-13
Sorry, I confused myself with your post. I didn't realize it was an ACPI problem. there's a kernel mode setting for setting ACPI I'll do what I can to look it up for you. Sorry about any confusion I caused.

---

### Post by -humanaut- on 2010-05-13
I found this I hope it helps. [http://wiki.archlinux.org/index.php/Intel](http://wiki.archlinux.org/index.php/Intel) check there KMS tips and tricks.

---

### Post by Nidwow on 2010-05-14
Thank you for the help and link.  Sorry, I didn't make it clearly.  My English is as bad as my Linux skill :P
 
I will read through it though it although it seem a little bit complicated for my skill but will read though them.

---

### Post by -humanaut- on 2010-05-14
If you want to improve you're Linux skills I highly recommend this website [http://tldp.org](http://tldp.org)
Good luck man.

---

