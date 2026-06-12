---
title: "Slow shut down"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by thgthg on 2009-02-10
After upgrading to 8.04 it takes several minutes for the PC to show the shut down dialog box to selecet restart, power of etc. Any one who know what to do??

---

### Post by avtolle on 2009-02-10
Is gnome power manager enabled in the start-up programs under System>Preferences>Sessions? If not, enable it; that solved my similar problem with 8.04. I wish I could recall the poster here that posted this, so I could give credit where it is due.

---

### Post by JK3mp on 2009-02-10
vary's on the amount of processes it has to shut down. Check your  manager..as stated above ;),lol

---

### Post by thgthg on 2009-02-11
OK, problem solved, case closed.
 Thank you for your help

---

### Post by bird_gal on 2009-03-14
> **avtolle said:**
> Is gnome power manager enabled in the start-up programs under System>Preferences>Sessions? If not, enable it; that solved my similar problem with 8.04. I wish I could recall the poster here that posted this, so I could give credit where it is due.

i have the same problem, computer takes forever to shut down. 
I can't find gnome power manager in my start-up programs, how do i add it? thanks

---

### Post by Linux000 on 2009-03-15
To add gnome power manager to your startup programs go to System/Preferences/Sessions click add under name type "Gnome Power Manager" and under command type "gnome-power-manager" you can make the comment whatever you want. Hope this helps.

---

### Post by bird_gal on 2009-03-15
thanks, i added the power manager. Just tried to shut down, unfortunately it still takes at least a full minute before the shut down menu appears.
any other ideas of what might be wrong?
thanks:)

---

### Post by Linux000 on 2009-03-15
What ubuntu are you using?

---

### Post by bird_gal on 2009-03-15
Ubuntu 8.04

---

### Post by Linux000 on 2009-03-16
Ok, good.
Go to System, Click Administration, Click System Monitor,
Then click on the processes tab, 
See if you can find Gnome power manager(The Icon is a battery and power cord)

---

### Post by Pappy1911 on 2009-03-16
I once had only 1 Gb of RAM and it took maybe 5-6 seconds to shut down.

I now have 3 Gb RAM and it shuts down almost immediately.

Possibly more processes are being held by the RAM. Maybe this will help.

---

### Post by bird_gal on 2009-03-16
Yep, it's there. Status says sleeping

---

### Post by bird_gal on 2009-03-16
yep it's there, status says sleeping.

---

### Post by Linux000 on 2009-03-16
Well... thats interesting, past that point I don't have a clue, sorry

---

### Post by bird_gal on 2009-03-16
thanks for your help tho:)

---

### Post by bird_gal on 2009-03-17
it's working now, funny. my computer just needed a day to have a think about it, apparantly;)

thanks guys

---

