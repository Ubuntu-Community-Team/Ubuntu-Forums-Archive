---
title: "Would like to adjust"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-06-16
the size of desktop icons....much smaller.  Can we do that?  9.04

---

### Post by ~sHyLoCk~ on 2009-06-16
> **Yed Ied said:**
> the size of desktop icons....much smaller.  Can we do that?  9.04

Right click on the icon and use "stretch icon"

---

### Post by Shibblet on 2009-06-16
Can you set all of your menu icons to be larger or smaller?

---

### Post by ad_267 on 2009-06-16
Your desktop is controlled by the file browser, Nautilus. Open up the file browser and go to Edit - Preferences - Views - Icon View Defaults and change the size.

---

### Post by Shibblet on 2009-06-16
> **ad_267 said:**
> Your desktop is controlled by the file browser, Nautilus. Open up the file browser and go to Edit - Preferences - Views - Icon View Defaults and change the size.

Thanks!

---

### Post by Yed Ied on 2009-06-16
Hate to be a dummy, actually I'm used to it, but I can't find nautilus.  Thanks

---

### Post by Shibblet on 2009-06-16
It's your file browser.

---

### Post by ~sHyLoCk~ on 2009-06-16
> **Yed Ied said:**
> Hate to be a dummy, actually I'm used to it, but I can't find nautilus.  Thanks

```
nautilus .
```

---

### Post by Locke_99GS on 2009-06-16
In GNOME, (which you probably have if you have your standard Ubuntu install) Nautilus is your file browser, as well as what draws the desktop. Just go to *Places > Home* from the top panel to open a file browser.

---

### Post by Yed Ied on 2009-06-16
I know it is my File Browser, I can't find the word NAUTILUS to open.  Sorry

---

### Post by ad_267 on 2009-06-16
> **Yed Ied said:**
> I know it is my File Browser, I can't find the word NAUTILUS to open.  Sorry

It's not actually called Nautilus anywhere. Just go to Places -> Home for example.

---

### Post by Shibblet on 2009-06-16
This is nautilus...

[IMG]http://polishlinux.org/reviews/ipod_i_linux/ipod_in_nautilus.png[/IMG]

---

### Post by Yed Ied on 2009-06-16
Thanks a bunch!!

---

### Post by Shibblet on 2009-06-17
> **ad_267 said:**
> Your desktop is controlled by the file browser, Nautilus. Open up the file browser and go to Edit - Preferences - Views - Icon View Defaults and change the size.

That works for the icons in Nautilus.  What about my menu icons?

---

### Post by ad_267 on 2009-06-17
> **Shibblet said:**
> That works for the icons in Nautilus.  What about my menu icons?

The original question was about desktop icons so that's what I was answering, I didn't see you asked about menu icons sorry. I think the icon size is controlled by the gtk theme you're using. If you're using the default Human theme you can edit /usr/share/themes/Human/gtk-2.0/gtkrc or if you're using a custom theme you can edit ~/.themes/THEMENAME/gtk-2.0/gtkrc.

The lines you have to change will depend on the theme. For the Human theme it looks like this line here needs to be changed:
```
gtk-icon-sizes = "panel-menu=24,24"
```

Alternatively, you could download a theme from gnome-look.org that uses smaller icons already.

---

