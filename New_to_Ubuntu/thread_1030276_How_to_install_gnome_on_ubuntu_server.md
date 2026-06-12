---
title: "How to install gnome on ubuntu server?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by drazgo on 2009-01-04
Hi there, 

I want to install a gui on my ubuntu server, but i don't know which packages i have to install in order to set up gnome. Can anyone help me with this please?

thanks in advance!
Drazgo

---

### Post by Michael.Godawski on 2009-01-04
hey

is the package ubuntu-desktop right for you? Or do you want to install only gnome?
```

sudo apt-get install ubuntu-desktop
```

Edit: I just wonder if my question was right or dumb.... hm

---

### Post by drazgo on 2009-01-04
i think that might do the trick, thanks! forgot there was such a meta package :P

---

### Post by mmercado on 2009-01-24
> **Michael.Godawski said:**
> hey

is the package ubuntu-desktop right for you? Or do you want to install only gnome?
```

sudo apt-get install ubuntu-desktop
```

Edit: I just wonder if my question was right or dumb.... hm

Hi Michael, your response helped me with the exact same question I had. Thank you. What is the difference between installing the ubuntu-desktop vs only gnome? I'm assuming that it has to do with all the tools/utilities/software that the desktop include... or what does installing only gnome mean? I'm completely new to ubuntu but I'm excited to learn more of it. I just finished installing the server version and waiting for the installation of ubuntu-desktop to finish.

---

### Post by perlluver on 2009-01-24
> **mmercado said:**
> Hi Michael, your response helped me with the exact same question I had. Thank you. What is the difference between installing the ubuntu-desktop vs only gnome? I'm assuming that it has to do with all the tools/utilities/software that the desktop include... or what does installing only gnome mean? I'm completely new to ubuntu but I'm excited to learn more of it. I just finished installing the server version and waiting for the installation of ubuntu-desktop to finish.

The difference is, Ubuntu-desktop brings with it, the Ubuntu theme, sounds, evolution, ubuntu settings, and all the system tools it uses.  Gnome-core, just brings the main features of Gnome, and is very slim.  I prefer the Ubuntu-desktop package myself.

---

### Post by mmercado on 2009-02-10
> **perlluver said:**
> The difference is, Ubuntu-desktop brings with it, the Ubuntu theme, sounds, evolution, ubuntu settings, and all the system tools it uses.  Gnome-core, just brings the main features of Gnome, and is very slim.  I prefer the Ubuntu-desktop package myself.

Gotcha... thanks perlluver!! I also love PERL but I haven't developed in such a long time... I'll probably get back to it. Have a good one :)

---

