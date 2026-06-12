---
title: "&quot;suspend &quot; dosnt work :/"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by neil_1 on 2011-04-03
when i hit suspend on the power actions tab,
the screen goes blank , random lines appear and then nothing i do gets it out of suspend  mode not even reisub :/
any ideas ?
edit:
i had to forcefully shutdown :(

---

### Post by ajgreeny on 2011-04-03
What hardware?

Some machines just refuse to go into standby/suspend, either automatically from power-manager settings, or manually from the shutdown dialog, mine included, but my machine is pretty old now, so no surprise there; it never did it in WinXP either.

---

### Post by neil_1 on 2011-04-03
hp dv6 laptop

---

### Post by neil_1 on 2011-06-12
*bump*
anyone know a work around ?

---

### Post by VOT Productions on 2011-06-12
Do you have a ATI Graphics card or a Intel Graphics card?

---

### Post by neil_1 on 2011-06-12
> **VOT Productions said:**
> Do you have a ATI Graphics card or a Intel Graphics card?
ati

---

### Post by wildmanne39 on 2011-06-12
> **neil_1 said:**
> *bump*
anyone know a work around ?
Hi, did you create a swap partition, you must have one for ubuntu to suspend.

---

### Post by Neoncamouflage on 2011-06-12
Hey. I have the same laptop, and seem to be encountering the same problem. I close the lid to make it hibernate and when I try to wake it up, black screen and flashing lights are all I get. But if I just leave it open and let it go to sleep itself from inactivity, it's all fine. I've just come into the habit of letting it do that.

---

### Post by neil_1 on 2011-06-13
> **wildmanne39 said:**
> Hi, did you create a swap partition, you must have one for ubuntu to suspend.
have a 4gb one
> **Neoncamouflage said:**
> Hey. I have the same laptop, and seem to be encountering the same problem. I close the lid to make it hibernate and when I try to wake it up, black screen and flashing lights are all I get. But if I just leave it open and let it go to sleep itself from inactivity, it's all fine. I've just come into the habit of letting it do that.
when you mean sleep from inactivity , do you mean the display turns off ?
thats what happens for me :/
it dosnt sleep , everything is running normally,just display is off

---

### Post by manzdagratiano on 2011-06-13
I had the same issue with my fiancee's laptop - it would not resume from suspend, and the solution was (courtesy of the Arch Linux wiki, don't remember which entry) to go into the BIOS and disable 'INTEL SPEEDSTEP'. After that, suspend from resume works like a charm.

---

