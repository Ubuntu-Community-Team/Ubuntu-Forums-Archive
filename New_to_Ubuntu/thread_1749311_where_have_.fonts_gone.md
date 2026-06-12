---
title: "where have .fonts gone?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by liatodua on 2011-05-04
I updated to ubuntu 11 and can not find .fonts folder any more to put some new ttf fonts there. Where is it?

---

### Post by wolfen69 on 2011-05-04
It's in usr/share/fonts/truetype

---

### Post by hhh on 2011-05-04
For a single user, you can also create the folder .fonts in your home directory.

---

### Post by liatodua on 2011-05-05
> **wolfen69 said:**
> It's in usr/share/fonts/truetype

Yes, I find this, but file manager does not allow me to add files to that directory.

---

### Post by krapp on 2011-05-05
You can see it in Nautilus by turning on "Show Hidden Files" (ctrl + H).

As for moving your fonts, drag them to the desktop, open a terminal window, and

```
cd Desktop
sudo mv filename location
```

---

### Post by liatodua on 2011-05-05
> **hhh said:**
> For a single user, you can also create the folder .fonts in your home directory.
It works, thank you

---

### Post by grahammechanical on 2011-05-05
You can also install fonts by clicking on the font file, selecting Open with Font viewer and then clicking Install Fonts. The work will be done for you.

Regards.

---

### Post by hhh on 2011-05-05
> **liatodua said:**
> It works, thank you
Your welcome. For working with system files, Alt+F2 then```
gksu nautilus
``` and BE FREAKING CAREFUL, YOU CAN HOSE YOUR SYSTEM!

---

