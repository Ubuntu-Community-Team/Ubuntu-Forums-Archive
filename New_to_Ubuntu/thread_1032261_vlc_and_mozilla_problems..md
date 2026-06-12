---
title: "vlc and mozilla problems."
date: 2009-01-06
forum: New to Ubuntu
---

### Post by harshpkaria on 2009-01-06
Using ubuntu 8.04.
--VLC is damn slow while maximizing/restoring and toggling to full screen.
--Youtube videos, when played in fullscreen, has a flickering sense and the contents of the page is seen in those flickering intervals. Also when pressing escape; the normal page does not load. 
Any help is severely appreciated.

---

### Post by thunk77 on 2009-01-06
Please provide some information so that others can help you. 
What are your system specs? 
What is your graphics card?
Do you have compiz enabled? 
What version of flash are you using? 
Do you play simultaneously flash and avi?

---

### Post by harshpkaria on 2009-01-06
Well... I am a newbie you see. Were can i see all these informations.
BTW,
I am using compiz effects extra normal with awn, also using flash and avi simultaneously, and graphics card and moterboard are from intel 945G. The graphic card is on board one.

---

### Post by thunk77 on 2009-01-06
I assume you are using GNOME as your window manager, so the simple way to see what your system specs are, is to go to the menu on your top left and select System -> Administration -> System Monitor, and click on the tab "System".

For a more detailed report, you must open a terminal window and type:

```
cat /proc/cpuinfo
```

then hit enter.

Generally it's not a good idea to run video files while surfing youtube for example in firefox, since flash doesn't cooperate very well while other video is playing.

However here's one thing you can try:
Open vlc, go to Settings -> Preferences, tick "Advanced Options" on the lower right side and select Video -> Output Modules on the left pane.
There is a dropdown list for "Video Output Module" you could try selecting "X11 video output", see if the problem persists and we'll take it from there.

---

### Post by harshpkaria on 2009-01-06
still the same problem persists...
It maximizes slowly
here is the content of /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) D CPU 2.80GHz
stepping	: 7
cpu MHz		: 2800.072
cache size	: 1024 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pebs bts pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips	: 5605.30
clflush size	: 64

The problem is:
Say the vlc runs in top left corner in a small window. Now when i maximize it; it still plays in that small windoe for a couple of SECONDS and then comes to the maximized window size, and the same happens for the 
fullscreen; but it plays well in "enlightment"
also RAM s just 512MB and all the "WOW" screen effects are ON.

---

### Post by harshpkaria on 2009-01-06
this problem is still unsolved. Please help

---

