---
title: "Intel Core 2 Duo 3GHz speed at 2.4GHz"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by MadsRH on 2009-07-08
Hi
Can anyone tell me if this is correct. I recently installed a new CPU (E8400) 3GHz Core 2 Duo. When I boot, the bios detects the right CPU but also writes speed 2.4 GHz :confused:

Is there some kind of setting that I need to adjust?
[ATTACH]120342[/ATTACH]



Thanks for reading

---

### Post by Paqman on 2009-07-08
Your CPU won't run at full frequency unless it's under high load. It's a power-saving feature. If you want to see how processor load affects CPU freq, install the CPU frequency monitor applet in a panel.

---

### Post by u-foka on 2009-07-08
check fsb and multiplier settings in bios!

maybe these are set to manual, or your mb somehow detects the settings wrong... but anyway you can play with them to get the correct setting!

refer to the mb's manual!

---

### Post by u-foka on 2009-07-08
> **Paqman said:**
> Your CPU won't run at full frequency unless it's under high load. It's a power-saving feature. If you want to see how processor load affects CPU freq, install the CPU frequency monitor applet in a panel.

but the bios shouldn't show the full frequency??

---

### Post by adam_kimber on 2009-07-08
I had this yesterday when I installed my Core Duo. E6850 at 3Ghz. It came up at 2.4Ghz. I changed the muliplyer and it seems to be fine. It steps up and down as it should.

---

### Post by HavocXphere on 2009-07-08
> **u-foka said:**
> but the bios shouldn't show the full frequency??
Yes. BIOS should show full ghz. Sometimes it also affects whether the named of the CPU is shown or not (AMD X ghz  vs AMD Athlon X ghz).

> **u-foka said:**
> check fsb and multiplier settings in bios!

maybe these are set to manual, or your mb somehow detects the settings wrong... but anyway you can play with them to get the correct setting!

refer to the mb's manual!
Either that or a physical jumper on the motherboard. (Mostly with older motherboards)

> **Paqman said:**
> Your CPU won't run at full frequency unless it's under high load. It's a power-saving feature. If you want to see how processor load affects CPU freq, install the CPU frequency monitor applet in a panel.
No. Not in the bios. It'll only affect the readings within the OS.

---

### Post by XCan on 2009-07-08
The FSB appears to be right as your ram report 5300 (667 MHz). So as other posters pointed out, it must be your multiplier that is incorrect.

---

### Post by MadsRH on 2009-07-30
Hi
Sorry for the late reply and thanks for all the feedback.

:confused: I can't find anything called "multiplier" in the BIOS settiings. This is what C*onfigure advanced CPU settings* looks like:
[ATTACH]122915[/ATTACH]

---

### Post by JohnLau on 2009-07-30
> **MadsRH said:**
> Hi
Sorry for the late reply and thanks for all the feedback.

:confused: I can't find anything called "multiplier" in the BIOS settiings. This is what C*onfigure advanced CPU settings* looks like:
[ATTACH]122915[/ATTACH]

I think the settings are correct...
It's kind of strange that it showed the correct FSB and [COLOR="Red"]correct multiplier(aka CPU RATIO)...[/COLOR]
What if you set the CPU Ratio to 9 manually?
John

---

### Post by mikechant on 2009-07-30
I guess you've done this already, but just in case - have you checked for a BIOS update on the relevant website?

---

### Post by MadsRH on 2009-07-31
**JohnLau** -> The CPU RATIO is already set to 9 - I'll try to see if the manual setting will change anything.

**mikechant** -> Yes, the bios is up to date

Thanks for the suggestions :confused:

---

### Post by XCan on 2009-07-31
Although according to your screenshot the ratio is already at 9, I think it could be worth it if you disabled speedstep just to see if it helps.

---

