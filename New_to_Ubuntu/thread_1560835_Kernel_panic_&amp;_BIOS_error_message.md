---
title: "Kernel panic &amp; BIOS error message"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Bearly Able on 2010-08-25
Hi all,

I've had no previous sign of a problem with my system, but when I tried to boot up just now, I got a "kernel panic" message.  I tried booting up again, using the recovery version, which seemed to go fine, except that I received a message to the effect that "your CPU has nx capabilities but this protection has been disabled in the BIOS" (or something along those lines).

I was far from enlightened, but rebooted and went into the BIOS, where I looked at every entry and couldn't find anything that looked like the right one.  The only item to do with the CPU that was showing as disabled was the temperature warning, so I enabled that for lack of other inspiration and everything seems to be hunky-dory.

Please could someone explain what the error message means and what I should actually have done, so I can fix things properly?

Thanks in advance.

Lesley

---

### Post by sydbat on 2010-08-25
> **Lesley Lutomski said:**
> Hi all,

I've had no previous sign of a problem with my system, but when I tried to boot up just now, I got a "kernel panic" message.  I tried booting up again, using the recovery version, which seemed to go fine, except that I received a message to the effect that "your CPU has nx capabilities but this protection has been disabled in the BIOS" (or something along those lines).

I was far from enlightened, but rebooted and went into the BIOS, where I looked at every entry and couldn't find anything that looked like the right one.  The only item to do with the CPU that was showing as disabled was the temperature warning, so I enabled that for lack of other inspiration and everything seems to be hunky-dory.

Please could someone explain what the error message means and what I should actually have done, so I can fix things properly?

Thanks in advance.

LesleyI wonder if some of your hardware is failing, specifically, your CPU. Can you tell us about the insides of your computer (CPU, RAM, etc)?

---

### Post by Bearly Able on 2010-08-25
I've had no previous sign of trouble, and the machine's not that old, so I hope it's not failing.  System specs attached - thanks for your help.

---

### Post by plucky on 2010-08-25
See [Here](https://bugs.launchpad.net/ubuntu/+source/cpu-checker/+bug/596963) and [Here](https://wiki.ubuntu.com/Security/CPUFeatures)

Good Luck

---

### Post by Bearly Able on 2010-08-25
Thanks, Plucky.  Your second link helped me to identify "Execute Disable" as the item I should have enabled, so that's it sorted now.  I still don't understand what caused the kernel panic, but everything seems to be fine.

---

