---
title: "How to get &quot;Software Sources&quot; into System-&gt;Adminstration"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by lennyw on 2009-01-11
Hi

I'd like to follow the instructions at [www.winehq.org/download/deb](www.winehq.org/download/deb) for installing a newer version of wine; but the instructions ask you to use "Software Sources" on the System->Administration menu. My 8.04 doesn't have such an entry.

Could someone give info on how to get "Software Sources" into that menu?

Thanks for your help!

Lenny Wintfeld

---

### Post by blackened on 2009-01-11
Alt+F2 -> alacarte

Go to System -> Administration and check the box for Software Sources. Close alacarte and check the menu, it should be there now.

---

### Post by amaroKer on 2009-01-11
You can also just open synaptic, and go Settings > Repositories.  Same deal.

---

### Post by lennyw on 2009-01-11
> **blackened said:**
> Alt+F2 -> alacarte

Go to System -> Administration and check the box for Software Sources. Close alacarte and check the menu, it should be there now.

>>>I already tried that. The problem is System->Administration doesn't have a selection of "Software Sources to check! How can I get Software Sources in to alacarte?


--Lenny

---

### Post by drs305 on 2009-01-11
> **lennyw said:**
> >>>I already tried that. The problem is System->Administration doesn't have a selection of "Software Sources to check! How can I get Software Sources in to alacarte?


--Lenny

The command in Intrepid to open Software Sources from System > Admin> Software Sources, which you could try in Hardy, is:
```
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/**software-properties-gtk**
```

If you need help in how to edit the menu via alacarte, just ask.

---

### Post by lennyw on 2009-01-11
> **amaroKer said:**
> You can also just open synaptic, and go Settings > Repositories.  Same deal.

The dialog only showed a list of ubuntu deb binary and source packages with scroll and new buttons.

 But that gave me an idea to use synaptic to search for "software sources" (using "Ctl-F"). From the resulting (long) list I took a stab at having synaptic install "software-properties-gtk". And it worked!! Now  "software sources" is in the System->Administration menu and it shows up instead of that simpler dialog when I select Synaptic->Settings->Repositories!!

I guess software-properties-gtk wasn't in my Ubuntu and I made a good guess.

Thanks for the hint.

--Lenny

---

### Post by blackened on 2009-01-11
Heh, weirdness. Glad you got it going, at any rate.

---

