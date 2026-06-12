---
title: "apt-get or aptitude?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by ags40 on 2009-11-04
Is there any advantage in using apt-get over aptitude? Thank you very much

---

### Post by LunaticHiatus on 2009-11-04
aptitude (I have been told) handles dependencies better. not much difference though. It also gives you suggestions if you typed in the wrong thing. For example, if you say 

sudo apt-get install panel

it will say:

E: Couldn't find package panel

If you say:

sudo aptitude install panel

it will say:

Couldn't find package "panel".  However, the following
packages contain "panel" in their name:
  libmoblin-panel-dev libgnomepanel2.24-cil hpoj-xojpanel 
  hildon-control-panel-l10n-english libmoblin-panel0-dbg op-panel 
  libpanel-app etc. etc. etc.

I find that pretty helpful.

---

### Post by ags40 on 2009-11-04
Tks LunaticHiatus.

---

### Post by LunaticHiatus on 2009-11-04
no problem, glad I could help

---

