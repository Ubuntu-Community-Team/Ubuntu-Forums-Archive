---
title: "Questions/Problems About Wine"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Kchymet on 2009-12-12
Ok, so I installed wine from the root terminal, and now I'm trying to upgrade my version from 1.1.31 to 1.1.34. I tried different methods of this through the terminal, but it hasn't been working.

Since then I've tried updating it through Ubuntu Software Center, but I keep getting this error upon clicking the upgrade button:

Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Details:
Wine

Losing any installed Windows programs is not an option, though because of my limited knowledge on Wine I'm not sure if any loss of data could occur by fixing this issue.

Can somebody help me with this?

Edit: Running Karmic 9.10 if that makes a difference.

I'm considering using
sudo apt-get remove wine
and then simply reinstalling it, but will I still have access to Windows applications I've installed if i reinstall Wine?

---

### Post by newbeeman on 2009-12-12
> **Kchymet said:**
> 
I'm considering using
sudo apt-get remove wine
and then simply reinstalling it, but will I still have access to Windows applications I've installed if i reinstall Wine?

I just had to re-install wine, it had disappeared leaving my Win programs disconnected.
I re-installed through Synaptic and the connections were remade.
I would suggest you remove via Synaptic, as it will take out any dependency errors, then do a reinstall the same way.

---

### Post by 3rdalbum on 2009-12-12
The software you installed in Wine is stored in your home directory. Synaptic will not touch your home directory, so the contents of .wine are safe.

---

