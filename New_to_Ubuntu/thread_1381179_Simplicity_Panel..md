---
title: "Simplicity Panel."
date: 2010-01-14
forum: New to Ubuntu
---

### Post by duds2008 on 2010-01-14
Hello people. This is probably an easy one, but I am pressed for time. My apologies for this. My parents are using "simplicity" based on mint (it's the one aimed at the elderly) As default it ships without the panel (task bar) on the desktop. How can I enable it?
Sincerest thanks in advance for any help, and once again apologies at the *most* probably easy solution.
Kind regards Dudley.

---

### Post by Maheriano on 2010-01-14
You need to specify more details on the problem, that doesn't make sense.

---

### Post by BandD on 2010-01-14
Do you know what DE (Gnome, KDE, etc.) Simplicity is based on?

---

### Post by arochester on 2010-01-14
Simplicity is the computer.

Mint is the Linux.

Eldy is the, Java, program which is supposed to make it more accessible to the elderly

YUK!

See [http://www.macworld.co.uk/digitallifestyle/news/index.cfm?newsid=27699](http://www.macworld.co.uk/digitallifestyle/news/index.cfm?newsid=27699)

---

### Post by ell02 on 2010-01-14
Try "alt F2". type in synaptic or control panel or some such to get to packages.gnome-panel should be what you want.
This is not absolute but the direction i would try, good luck.

---

### Post by J V on 2010-01-14
rightclick desktop add panel?

---

### Post by duds2008 on 2010-01-15
> **BandD said:**
> Do you know what DE (Gnome, KDE, etc.) Simplicity is based on?
Gnome

---

### Post by duds2008 on 2010-01-15
> **J V said:**
> rightclick desktop add panel?

This does not work. Tried it already. Thanks anyway.

---

### Post by duds2008 on 2010-01-15
> **arochester said:**
> Simplicity is the computer.

Mint is the Linux.

Eldy is the, Java, program which is supposed to make it more accessible to the elderly

YUK!

See [http://www.macworld.co.uk/digitallifestyle/news/index.cfm?newsid=27699](http://www.macworld.co.uk/digitallifestyle/news/index.cfm?newsid=27699)

They went out and bought this "simplicity". I had no idea about it. I agree that it is yuk. !

---

### Post by zeroseven0183 on 2010-01-15
Try this one: [http://superuser.com/questions/82822/panel-bar-deleted-in-linux-mint-gloria](http://superuser.com/questions/82822/panel-bar-deleted-in-linux-mint-gloria)

Or you can press ALT + F2 then type gconf-editor.
Look for **required_components_list** in **desktop** > **gnome** > **session**
then add **gnome-panel** in the panel field

---

### Post by duds2008 on 2010-01-15
> **Maheriano said:**
> You need to specify more details on the problem, that doesn't make sense.

I am sorry. Your answer does not make sense.

---

### Post by duds2008 on 2010-01-15
> **ell02 said:**
> Try "alt F2". type in synaptic or control panel or some such to get to packages.gnome-panel should be what you want.
This is not absolute but the direction i would try, good luck.

Thank you! This is by far the most sensible answer I have received. I tried apt-cache search gnome-panel. Loads of results! Will try this later on tonight as am heading off to work in the next few minutes. Thanks. Will let you know if this works!!

---

