---
title: "Does Anyone Know Which Packages Interfere with Compiz?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by lhb1142 on 2009-07-05
This morning I installed a great many audio and video codecs and programs from the Synaptic Package Manager.

Previous to installing these, the CompizConfig Settings Manager and the Simple CompizConfig Settings Manager both worked perfectly and allowed me to have a Custom set of visual effects installed and operating.

Since I installed these new programs, the Custom visual effects is disabled and I cannot have these effects operating.

While this is certainly not earth-shattering, I should like to know if anyone knows which specific audio and/or video codecs and/or programs are positively known to interfere with Compiz.

Thanks for any help. ):P

---

### Post by sdlynx on 2009-07-05
I haven't heard of any codecs that can do that but one time I had to run ccsm as root to change the compiz settings (don't really know why but it worked).  Maybe try that?

---

### Post by lhb1142 on 2009-07-05
I should have added that I am using an Acer Extensa 5620-6419 (Intel Core 2 Duo Processor T5550, 3 GB DDR2) running Ubuntu 9.04 'Jaunty Jackalope.'

It is obvious that at least ONE of the programs I installed this morning from the Synaptics Package Manager has disabled Compiz and Simple CCSM; I should just like to know if anyone knows which such programs can/will do this. ):P

---

### Post by drs305 on 2009-07-05
If any of these apps turned on metacity compositing, it must be turned off before you can switch to compiz. Run this command to turn off metacity compositing (if it is on you will have 'shadows' around your window borders).

The symptoms would be you select Normal or Advanced in System, Preferences, Appearance but it returns to 'None' after the screen blinks/resets several times.

```

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager false

```

---

