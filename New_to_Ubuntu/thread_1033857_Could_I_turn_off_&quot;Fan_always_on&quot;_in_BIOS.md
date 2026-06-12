---
title: "Could I turn off &quot;Fan always on&quot; in BIOS?"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Adamantus on 2009-01-07
My computer is an HP dv5-1004nr and I'm running Hardy Heron. I have a cpu frequency governor installed that usually keeps my processor (AMD Turion X2 2.1 GHz) at about only 500 MHz and the fan relatively quiet, but my fan is always on no matter what, even when the computer is just sitting there. It gets kind of annoying, so I looked in the BIOS and there is an option that says "Fan Always On" which is checked. Would it be okay for me to uncheck it, or would it hurt my computer?

Also, I've been hearing this high pitched noise (it's hardly noticeable) that I'm pretty sure is from the fan running too much, since it only starts after my computer has been running for awhile (another reason why I want the fan to be able to turn off).

---

### Post by oilchangeguy on 2009-01-07
> **Adamantus said:**
> My computer is an HP dv5-1004nr and I'm running Hardy Heron. I have a cpu frequency governor installed that usually keeps my processor (AMD Turion X2 2.1 GHz) at about only 500 MHz and the fan relatively quiet, but my fan is always on no matter what, even when the computer is just sitting there. It gets kind of annoying, so I looked in the BIOS and there is an option that says "Fan Always On" which is checked. Would it be okay for me to uncheck it, or would it hurt my computer?

Also, I've been hearing this high pitched noise (it's hardly noticeable) that I'm pretty sure is from the fan running too much, since it only starts after my computer has been running for awhile (another reason why I want the fan to be able to turn off).

i'd suggest leaving the fan on. and why do you have your cpu chocked down to 500mhz?

---

### Post by oilchangeguy on 2009-01-07
i just googled your computer. and have you considered that you are probably driving your computer insane by having the cpu at 500mhz? what is the point? undo what you have done. let the cpu do what it was designed to do. it's probably overheating, because you've got it at 500mhz. trying to do what a 2.1ghz. cpu is supposed to do.

---

### Post by Adamantus on 2009-01-07
I don't have it set to 500 MHz. It's set to 'On Demand', so it's only using what it needs. It goes up to 1.0 and 2.1 GHz when needed, but it's only for split seconds when a program is opening or a flash player movie is playing. If I set it up to 2.1 GHz, the fan gets extremely loud.

---

### Post by Paqman on 2009-01-07
I'm assuming that that option in BIOS simply allows the fan to come to a full stop if the CPU temp is low enough.

Do you have temperature monitoring available in your BIOS? If so, then you could uncheck "fan always on" and then sit at the temp monitoring page and watch the temps. If they start climbing then switch the setting back on immediately.

There's also a good temperature monitoring tool in the repos called sensors-applet. It'll sit on a panel and show various temps like CPU/GPU/drives. You may need to run:
```

sudo sensors-detect

```

after adding it to the panel.

---

### Post by Adamantus on 2009-01-12
I apparently don't have any sensors, which I think is kind of weird. I tried "lm-sensors" and it couldn't detect anything. 

Anyway, could I possibly try it then feel case and turn it off if it feels too hot? Or is that too risky? It's really not that bad at all and wouldn't want to risk hurting my computer if there's even around a 15% of hurting it.

---

