---
title: "Desktop Effects"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-11-04
Hello, I just want to ask, I couldn't activate even the normal desktop effects on my computer even though I had the advanced desktop effects this happened after messing up my computer trying to install the 3d driver for ATI x1650SE. I just really like the desktop effects this is a screen shot from my computer.
[IMG]http://img257.imageshack.us/img257/5852/screenshotrw.th.png[/IMG]

---

### Post by nikhilup on 2009-11-04
Do you have the drivers installed....?

---

### Post by Ant59 on 2009-11-04
Run

```
compiz --replace
```in the terminal.

Post the output.

---

### Post by SunnyRabbiera on 2009-11-04
There seems to b e issues with Karmic+ATI, the ATI drivers are a pain in the @$%^ anyhow

---

### Post by Ant59 on 2009-11-04
> **SunnyRabbiera said:**
> There seems to b e issues with Karmic+ATI, the ATI drivers are a pain in the @$%^ anyhow

Really? My ATi card worked out-of-the-box just by installing the suggested proprietry drivers.

---

### Post by Bimps on 2009-11-04
> **Ant59 said:**
> Run

```
compiz --repalce
```in the terminal.

Post the output.

Typo in the command above. In case the OP cuts and pastes the command:

```
compiz --replace
```

---

### Post by Ant59 on 2009-11-04
> **Bimps said:**
> Typo in the command above. In case the OP cuts and pastes the command:

```
compiz --replace
```

Whoops! Really sorry! I'm always typing "replace" wrong.

---

### Post by ajgreeny on 2009-11-04
> **SunnyRabbiera said:**
> There seems to b e issues with Karmic+ATI, the ATI drivers are a pain in the @$%^ anyhow
Until karmic, the opensource ati/radeon driver provided by the system at install was absolutely great with my card (9200SE), running full compiz effects without a murmur.

Karmic has, as you say, upset that situation and degraded the usefulness of my card, requiring either no compiz running, or reduced resolution of 1024x768, or 16 bit colour instead of 24 bit.  I don't know specificaly about the OP's card and proprietary drivers, but mine will not use any of them and needs the OP version, which is the broken one.

---

### Post by LADmaticCA on 2009-11-04
I just install karmic today on my test machine running an ATI X800 and I'm having the same problems. Right now desktop effects are on but seems overall slower than it did on jaunty. I can barely scroll down a youtube page without major slow-down...could be slow flash in that case; but yes I have trouble enabling effects and I lose them on reboot.

---

### Post by LewRockwell on 2009-11-04
> **ajgreeny said:**
> Until karmic, the opensource ati/radeon driver provided by the system at install was absolutely great with my card (9200SE), running full compiz effects without a murmur.

Karmic has, as you say, upset that situation and degraded the usefulness of my card, requiring either no compiz running, or reduced resolution of 1024x768, or 16 bit colour instead of 24 bit.  I don't know specificaly about the OP's card and proprietary drivers, but mine will not use any of them and needs the OP version, which is the broken one.

you are not alone...lol

.

---

### Post by mosaabJ on 2009-11-05
> **Ant59 said:**
> Run

```
compiz --replace
```in the terminal.

Post the output.

This what I got:

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by Ant59 on 2009-11-05
So, you tryed to install the ATi drivers, and weren't able to? You need to install those drivers to enable compiz effects.

---

### Post by pablolie on 2009-11-05
from my own experience with nvidia drivers, the best thing to do after installation is to wait until the system prompts you to install what they label as "proprietary drivers" with a warning that they might not be open source and what not. 

i certainly do hope 9.10 did not break ATI driver support, because i just told an acquaintance with the exact same card mentioned in this thread twice to upgrade, since my own experience with 9.10 has been trouble-free. :-o

---

### Post by uberg on 2009-11-05
My experience with 9.10 and the suggested drivers under "Hardware Drivers" worked just fine.  ATI.

---

### Post by mosaabJ on 2009-11-05
> **Ant59 said:**
> So, you tryed to install the ATi drivers, and weren't able to? You need to install those drivers to enable compiz effects.
Can you please explain more

---

### Post by tomski on 2009-11-05
hi guy's

i have similar problems with a nvidia card
geforce 940 GT

the nvidia driver is loaded

ran 
$ compiz --replace 
aborting and using fallback: /usr/bin/metacity 

then it hung
ctrl+c

now i have lost my window borders nice one!!!

---

### Post by mosaabJ on 2009-11-05
I sorted my problem with the desktop effects by reinstalling the Open source driver. I followed steps from this URL is [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver"), I just want to ask for Radeon x1650SE if I configure my xorg.conf will it activate the 3D graphics as I did this before but didn't work (I think I've done something wrong).

---

