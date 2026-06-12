---
title: "Can't shut down/No sound"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by catsails on 2010-07-04
Hello all,

just did a fresh install of 10.04 on an acer aspire laptop. Attempting to shut down or reboot would just bring me back to the login screen, and I had no sound. I fixed this with sudo reboot, but the same thing ocasionally happened when I had ubuntu installed with wubi. Is there a permanent fix to this? I have sound working now, but I don't much like the idea that ubuntu will decide to not have sound or let me shut down whenever it wants.

---

### Post by Lorraine Swingaroo on 2010-08-03
I'm having the same problem on occasional shutdowns.
I notice that there is no sound, no sound card found, then it won't shutdown. It just restarts with the same sound problem.

If I do a full shutdown by holding the power button, it comes back with full sound.

I dj from this HP laptop so need to resolve this problem. Please help?

---

### Post by neilms on 2010-08-04
The shutdown problem is due to acpi, which you need to set to off. I'm not sure how you do it but it only involves editing one file with the line acpi=off.
I had the same problem with sound that I never fixed, but you need to try all the tutorials. In my case I think there is a bug in the sound driver code.

---

### Post by Lorraine Swingaroo on 2010-08-04
Thanks. 

As a side note, I've now set the power manager to shut down when I close the lid. It's only been a couple of days but the problem hasn't recurred since.

---

### Post by ariadacapo on 2010-08-05
I’m affected too, same symptoms. 

See also [Thread 9681464](http://georgia.ubuntuforums.org/showthread.php?p=9681464) for further discussion.

---

### Post by ariadacapo on 2010-08-05
Ah, it seems this is bug [#544139]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/"). Please check it out, and indicate that it affects you if this is the case...

---

