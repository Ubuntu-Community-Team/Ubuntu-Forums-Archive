---
title: "disable update on certain app"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by launchy on 2010-06-16
hi, i recently uninstalled evolution mail client because i dont use it but i am now getting updates for this program. how can i disable upcoming updates of evolution or any particular app that i have uninstalled?

---

### Post by ubunterooster on 2010-06-16
Evolution _mail_ is gone but Evolution is not just mail.

Evolution-data server-common just had an update and that is a part very  deeply integrated into Ubuntu that would remove your entire gnome  session if you removed it

---

### Post by launchy on 2010-06-16
hmmm im a bit confused. so when i uninstalled evolution through ubuntu tweak software. what was uninstalled?

---

### Post by ubunterooster on 2010-06-16
the package named "evolution" which is used to get mail was removed. Other evolution-based pakages were not removed as removing some of them would stop the GUI from working (I did that once :()

---

### Post by k3lt01 on 2010-06-16
It depends on what you asked to be removed. There are 5 different packages for Evolution that are part of the default install.

The best way to uninstall anything is through Synaptic. It will let you know what will be removed when you select a package to uninstall.

To answer your original question you can "pin" a package so it will not update. You do this through Synaptic.

---

### Post by 3rdalbum on 2010-06-16
> **launchy said:**
> hmmm im a bit confused. so when i uninstalled evolution through ubuntu tweak software. what was uninstalled?

Evolution   is  in   two   parts.   One   part   is   the   e-mail   program  itself,   the  other   smaller  part  provides   other   services   to   the   system  and   cannot   be   easily   removed.  This   part   will   still  receive   updates  unless you   use  the  'lock  version'  feature  of  Synaptic.

WARNING:  Before   removing  anything in Synaptic,   it will give you a list of what dependent packages will be removed also. Check this list carefully! If it is a long list then you probably do NOT want to procede as it may be removing half of your system!

You  won't  get  updates   to  the   main  Evolution  program,  because  it  is  not  installed.

---

### Post by launchy on 2010-06-16
oh ok thanks. i guess i will install evolution again and unistall it through synaptic to see what packages come with it and what i can remove safely without compromising the GUI.

---

