---
title: "Asrock Intel i7 Z68 Pro 3 Gen 3 - Realtek rtl8111/8168/8411"
date: 2020-11-16
forum: Networking &amp; Wireless
---

### Post by electrosteam on 2020-11-16
Attempting resurrection of a troublesome mobo from several years ago to be used as a backup controller for my cnc mill.

Tried two hard drives and a few flavours - all give problems.
Lubuntu 20.04.1 survives about an hour without net connection, then freezes.
Lubuntu 18.04.1 got 26 hours without net, then tried net connection with freeze within 5 minutes.
Ubuntu Mate similar.

The existing net details with sudo lshw may be:
controller;
 RTL8111/8168/8411,
driver;
  r8169 version version 2.3LK - NAPI,
firmware;
 rtl8168e-3_0.0.4  03/27/12.

My next effort will be to get a Network Interface Card, perhaps the Intel PRO/100.

Alternative suggestions welcomed.

Keep well,
John.

---

### Post by DuckHook on 2020-11-16
The phrase "troublesome MOBO from several years ago" bodes nothing but disaster.

You go on to describe symptoms so cringe&#8209;inducing that they all but confirm this pessimistic assessment.

Only you can decide how much your time and frustration are worth, but having dealt with "troublesome MOBOs" in the past, anything questionable I just throw in the river. Well&#8230; not actually in the river, but you get my drift. Such problems can be caused by anything: hairline cracks, burned out capacitors, bad BIOS chips&#8212;the list is as long as my arm and always almost impossible to nail down. Life is just too short to spend it playing whack&#8209;a&#8209;mole.

Given your use case, I would be especially reluctant. CNC Milling appears to be a real&#8209;time, exacting and mission critical process that demands utter reliability and robustness in all components. Do you really want to entrust such important processes to the HW equivalent of Your Crazy Uncle?

You asked for alternative suggestions. Mine would be, buy new rock solid components, stress test the bejeezers out of them, then implement with replacements and backups.

This MOBO should be nuked from orbit.

Best Regards,
DH

---

### Post by electrosteam on 2020-11-16
DuckHook
Your thoughts on the subject are well founded, and will probably be followed.

I was hoping that the particular RealTek chipset were known to cause problems, even when not connected to the net.

Rest easy, a good hard cnc mill controller is on hand.
A RaspBerry Pi 4B with 8GB RAM has been acquired and is operational with the native OS.
Next will be a SSD and then battle commenced to get LinuxCNC embedded on it.
Once operational, a spare one will be shelved as back-up.

Keep well,
John.

---

### Post by DuckHook on 2020-11-16
Good to hear. It amazes me how many things can be done on those little R-Pis.

Good Luck and Happy Ubuntu-ing!

---

