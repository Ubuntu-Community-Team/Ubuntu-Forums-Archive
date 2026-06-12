---
title: "Work around for the dreaded &quot;cannot find /dev/dsp&quot; error"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by arvevans on 2011-02-15
For several months I have been trying to find a way to run older apps from the Ubuntu repository which rely on the presence of /dev/dsp as a standard location for hooks into the audio system.  I even posted several threads here on Ubuntu forums which received many looks but no suggestions of a solution.

Yesterday I found a work-around that seems to make those older applications usable again.  It is hidden inside an installable application called "pulseaudio-utils"  and is the command "padsp".  You have to install pulseaudio-utils, then launch your commands which require /dev/dsp by prefixing them with

[INDENT]** padsp [application name]** [/INDENT]

This lets many of the otherwise useless legacy applications remain usable in recent distributions of Ubuntu.  Remember that this is a "work-around" and not a real fix for the missing /dev/dsp.  Hopefully someone at Ubuntu will eventually decide to write a shim program called /dev/dsp that will make this non-standard launch method unnecessary.

---

### Post by pmpope on 2011-11-28
Thanks for the workaround :) It works like a top =D>

---

