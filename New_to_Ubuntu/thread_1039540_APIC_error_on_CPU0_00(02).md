---
title: "APIC error on CPU0: 00(02)"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by kestrel1 on 2009-01-14
Does anyone know what this error means:```
 APIC error on CPU0: 00(02)
```
I keep getting a message up during boot so I ran dmesg & that is the last entry in the list.
Anyway, any ideas.
Thanks

---

### Post by Crafty Kisses on 2009-01-14
Not sure what your specs are, but usually that error presumes with hardware problems, don't worry about it unless it's actually causing you problems. You might just have some marginal hardware, or questionable hardware. Not a big deal, you could always compile a newer kernel and see if you get the problem still.

---

### Post by kestrel1 on 2009-01-14
Thanks for that. I think you may be right, I just rebooted & didn't get the message at login & just run dmesg & it is not there.
Cheers

I would have sent a thanks & mark the thread solved, but for some reason I haven't got either option at present. Rather strange.

---

### Post by Coreigh on 2009-01-14
You can add "NOAPIC" to the boot arguments to disable APIC features. There is another command that can disable other power management features; "acpi=off"

Here is a link about the NOAPIC:
[http://ubuntuforums.org/archive/index.php/t-148761.html](http://ubuntuforums.org/archive/index.php/t-148761.html)

You can also do some "googling" just search for noapic.

---

### Post by kestrel1 on 2009-01-15
If I get the problem again I will do that.
Many thanks

---

