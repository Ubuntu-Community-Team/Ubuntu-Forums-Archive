---
title: "ACER 5670 0verheating"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by renata.a on 2010-11-28
Hi,

I am trying ubuntu maverick i686 release in an old acer 5670, but the laptop overheats really fast under load.
I also have windows, and I do not get the problem there. I ve noticed that the fan runs faster on Windows (I can hear it..)

I have searched a lot here, and tryed a lot of things, like acpi.power_nocheck, I have the latest bios from acer (bios for windows vista or something like that).

Oh, here is my THRM/trip_points file:

critical (S5):           97 C
passive:                 93 C: tc1=2 tc2=3 tsp=40 devices=CPU0 

I am not sure, but does it have no active trip points? 

Also, I do not have battery anymore (it is an old laptop) and I opened it to clean the pipes (as I said, windows xp does not have this problem... it is HOT, but not OVERHOT :P)

Can anyone help me to run maverick smoothly?

---

### Post by Wobblybob on 2010-11-29
Hi Mate I have the same lappy running Lynx as a server so can't help with Maverick. I found it started shutting down for no aparent reason and eventually found the processor temp got to 99+ and then died. I removed the plate over the fan and found it stuffed with dust etc. Once removed the temp on continous running is 40-50 and no shutdowns.

---

### Post by ibizatunes on 2010-11-29
try a bios / firmware update, i had something similar and then it was fix with a firmware update.....

---

### Post by renata.a on 2010-12-02
Sorry guys,

I have cleaned the fan and pipes already, and I am using the latest bios avaliable, but these did not help at all.
Using windows I can hear fan running louder than maverick when the temperature is above 80 C

Any other suggestions?

---

### Post by SebSmith on 2010-12-02
> **renata.a said:**
> Sorry guys,

I have cleaned the fan and pipes already, and I am using the latest bios avaliable, but these did not help at all.
Using windows I can hear fan running louder than maverick when the temperature is above 80 C

Any other suggestions?


did you disassemble your computer to clean the fan from the inside?

---

### Post by renata.a on 2010-12-03
> **SebSmith said:**
> did you disassemble your computer to clean the fan from the inside?

Yes I did.

Sometimes the fan starts to go faster early (like 70 C), but I could not find a pattern yet.

---

