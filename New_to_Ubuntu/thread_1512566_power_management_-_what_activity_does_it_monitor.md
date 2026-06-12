---
title: "power management - what activity does it monitor?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by kenmac2 on 2010-06-18
Hi folks,
What "activity" is the Power management function monitoring?
I can set it to a time, and it works, as long as absolutely nothing is happening.
However, if I run a slideshow continuously, it fails to trigger.
From this I assume it must watch the HDD activity.
Is there a way to tell it to only look at the mouse/keyboard and ignore the HDD?
I previously used a Win 98 PC which did allow this.

kenmac2

---

### Post by kenmac2 on 2010-06-18
Anyone able to help here?

kenmac2

---

### Post by kerry_s on 2010-06-18
it monitors acpi events. it doesn't start counting till theres no activity.

some programs have settings to disable power management & screen saver when running, so you might want to check those settings in the program your your using.

---

### Post by kenmac2 on 2010-06-19
I had a look at the ACPI info, but there doesn't seem to be anything specific to monitoring the mouse/keyboard activity.
A lot of the scripts are associated with Laptop stuff, like lid closure.
Perhaps "activity" refers to the data bus actions?
Is there a way to monitor mouse clicks over a preset time and cause the monitor to sleep when none (clicks) are detected?
As I said before, it was possible on the original  Win 98 PC, using the power monitoring options.
It has now been upgraded to an IBM P4, with Ubunutu 9.04 installed.
The PC is used for a public slideshow, which runs continuously.
Previously we used a motion detector connected across the mouse LH switch to "revive" the sleeping monitor.

kenmac2

---

### Post by t.n.a. on 2011-11-14
I don't suppose remote ssh sessions would prevent it from going into power-save? How would one reset the timer remotely?

To clarify, I would like to set up a relatively short period (~30min) to a power-save state, but I would like to be able to periodically reset the timer remotely to keep the machine running as long as I need it.

Any suggestions?

---

