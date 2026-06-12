---
title: "Won't turn off."
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Roadbloc on 2009-01-27
I have a compaq presario 1700us and whenever i shutdown with ubuntu, it doesn't automaticly switch off the machine, i have to press and hold the power button when i am sure it has finished, and the same with hibernating. 

I was just wondering if there was a way to get it to turn off automaticly becuase it is a bit annoying....   :-k

---

### Post by drs305 on 2009-01-27
Close all open apps and try running this command, which should shut down and power off your machine in an orderly fashion. If it works you can make a shortcut with the command and put it on the panel although I would continue to try to find a solution as to why it won't shut down with the normal icon.

```
sudo shutdown -P now
```

---

### Post by philinux on 2009-01-27
> **Roadbloc said:**
> I have a compaq presario 1700us and whenever i shutdown with ubuntu, it doesn't automaticly switch off the machine, i have to press and hold the power button when i am sure it has finished, and the same with hibernating. 

I was just wondering if there was a way to get it to turn off automaticly becuase it is a bit annoying....   :-k

How old is the machine. You may need to add acpi=force to the kernel line in grub.

---

### Post by Roadbloc on 2009-01-27
The machine is a pentium compaq presario 1700us. I am afraid i know knothing else.:(

---

### Post by sydbat on 2009-01-27
> **Roadbloc said:**
> The machine is a pentium compaq presario 1700us. I am afraid i know knothing else.:(This looks like your machine - [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00255606&lc=en&dlc=en&cc=us&product=95250](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00255606&lc=en&dlc=en&cc=us&product=95250)

I had a similar problem with an older box...it would never shut off, but would reboot instead, so I had to hold down the power button. Even updating the BIOS did not help. It *may* be something you have to live with...sorry.

---

