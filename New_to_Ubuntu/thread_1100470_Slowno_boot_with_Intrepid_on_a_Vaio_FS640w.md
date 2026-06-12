---
title: "Slow/no boot with Intrepid on a Vaio FS640/w"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by MooGoo on 2009-03-19
Hi everyone,
I'm new to the forums and to ubuntu. I'm having a hard time starting ubuntu when I hit the start button on my laptop. Sometimes it 15 min or longer to load. However once ubuntu is up and running I can restart and/or shut down and start up without any trouble. Any ideas on how to solve this? I've downloaded the boot log thingy and next time it happens I'll post it on the forums if it helps. It may be important to this happens before I get the Vaio boot screen and also sometimes after it.  The screen just stays black.  I've also seen some posts about changing something from splash to nosplash but this was for Gutsy so im not sure if i should do that 
Thanks,
Moo Goo

---

### Post by Temposs on 2009-03-19
Did you actually install Ubuntu or are you just trying to run it from the CD?

---

### Post by paultag on 2009-03-19
> **MooGoo said:**
> Hi everyone,
I'm new to the forums and to ubuntu. I'm having a hard time starting ubuntu when I hit the start button on my laptop. Sometimes it 15 min or longer to load. However once ubuntu is up and running I can restart and/or shut down and start up without any trouble. Any ideas on how to solve this? I've downloaded the boot log thingy and next time it happens I'll post it on the forums if it helps. It may be important to this happens before I get the Vaio boot screen and also sometimes after it.  The screen just stays black.  I've also seen some posts about changing something from splash to nosplash but this was for Gutsy so im not sure if i should do that 
Thanks,
Moo Goo

First of all, Welcome :)

Second of all, a boot log would be nice. Please post it.

Third of all, please do change the boot to nosplash. it will give you / us great insight into what is going on besides a nice pretty orange bar going back and forth.

that can be found in /boot/grub/menu.lst

Cheers,
Tag

---

### Post by MooGoo on 2009-03-19
FYI it's installed as the only operating sys.  Changed the splash to no splash. so far so good...

---

### Post by MooGoo on 2009-03-22
ok so here are boot charts of a successful start and a not so successful one

---

### Post by paultag on 2009-03-24
oh dear god.

Modprobe is doing something _nasty_

There is something wrong with that kernel...

Please file this as a bug on Launchpad... Be sure to include these dumps.

Best of Luck,
Tag

---

