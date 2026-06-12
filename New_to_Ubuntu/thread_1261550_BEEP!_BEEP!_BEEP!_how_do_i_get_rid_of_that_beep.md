---
title: "BEEP! BEEP! BEEP! how do i get rid of that beep?"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-08
i have it blacklisted and the unchecked "use sound to notfy me of error" in  power management preferences[COLOR=Red]> needed to restart[/COLOR].

---

### Post by dustins on 2009-09-08
Does executing "sudo rmmod pcspkr" stop the beeping or is it a deeper issue than that?

---

### Post by oldsoundguy on 2009-09-08
if this is happening on boot:
[http://www.pchell.com/hardware/beepcodes.shtml](http://www.pchell.com/hardware/beepcodes.shtml)

---

### Post by pythonscript on 2009-09-08
Never mind. I didn't see when you said you had it blacklisted.

---

### Post by R3fr4cti0n on 2009-09-08
> **dustins said:**
> Does executing "sudo rmmod pcspkr" stop the beeping or is it a deeper issue than that?

```
julian@Abriella:~$ sudo rmmod pcspkr
ERROR: Module pcspkr does not exist in /proc/modules

```

darn.

---

### Post by Geocron on 2009-09-10
go to system>preferences>sound then on 2 tab (sounds) unclick "play alert sound"
that got rid of the beeping for me

---

### Post by credobyte on 2009-09-10
[http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/](http://ubuntu-tutorials.com/2007/07/26/turning-off-the-system-hardware-beep-linux-tutorial/)

---

