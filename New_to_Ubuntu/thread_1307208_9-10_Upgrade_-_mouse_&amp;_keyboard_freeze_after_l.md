---
title: "9-10 Upgrade - mouse &amp; keyboard freeze after login"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by CountryFan on 2009-10-30
I've just upgraded from 9-04 Jaunty to 9-10 Karmic. The system boots and seems to recognize the mouse at first, but immediately after moving the cursor, it freezes and I can get no more mouse or keyboard input. This has happened on each of several reboots.

I've discovered that if I skip the default boot to 2.6 31 14 generic kernel, and boot instead to 2.6 28 16, this problem does not occur and I can use programs and access the internet (however, then I have no sound)

I have no real knowledge about the different kernels (booting into the second one was just a guess - it says "loading restricted drivers", so I presume it's meant mainly for emergencies), and I'm hoping someone can help me get full use of the default kernel.

Thanks if anyone understands this problem

---

### Post by gizmobay on 2009-10-31
I know my first boot took awhile after I entered my user and pass. It was so bad I thought the whole system froze and twice I did a REISUB. Once I walked away, and came back and then did a reboot no problems.

---

### Post by CountryFan on 2009-10-31
Thanks - but I'm getting this problem every time. Karmic boots, and I get to the desktop, apparently normally. I can move the cursor with the mouse a short distance - but as soon as I approach the task bar to start a program, the cursor freezes and I can get no more input from either mouse or keyboard. I can only restart by using the computer reset button, and then the same thing happens.

I'm only on the internet now by booting into the second Linux kernel menu option, which seems to give fair, but restricted functionality.

---

### Post by CountryFan on 2009-10-31
Well, I haven't been able to resolve this - and I'm guessing it must be an unusual problem. 

I'm still using the new Karmic upgrade, but in the boot menu's reserve option (kernel 2.6 28 16 generic). This one does work - but I can't stay in it, as it has no sound (and doesn't seem to have any obvious options that I can find for tweaking sound - it just has blanks under sound devices)

I still have the disc I made for Intrepid, and if this can't be resolved, I think I'll reinstall Intrepid, and maybe upgrade to Jaunty from there. (Intrepid and Jaunty both worked on my system, without the problem I've just encountered)

---

### Post by LewRockwell on 2009-10-31
> **CountryFan said:**
> Well, I haven't been able to resolve this - and I'm guessing it must be an unusual problem.

You aren't alone, you're just lucky enough to be able to still use the interwebs to contact the rest of the Krippled Karmic Koalas out here...hahaha

> **CountryFan said:**
> I'm still using the new Karmic upgrade, but in the boot menu's reserve option (kernel 2.6 28 16 generic). This one does work - but I can't stay in it, as it has no sound (and doesn't seem to have any obvious options that I can find for tweaking sound - it just has blanks under sound devices)

Cool triage

> **CountryFan said:**
> I still have the disc I made for Intrepid, and if this can't be resolved, I think I'll reinstall Intrepid, and maybe upgrade to Jaunty from there. (Intrepid and Jaunty both worked on my system, without the problem I've just encountered)

You should get a Jaunty LiveCD and use it to install

We sure wish the default for Compiz was OFF because we're still seeing and receiving bad reports until folks can get it turned OFF

.

---

