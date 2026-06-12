---
title: "Volume Icon Missing"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by nebu on 2010-06-21
I deleted the evolution mail icon on the menubar at the top of the screen and inadvertently deleted the volume/speaker icon also....

How do I get it back? What should I do?

---

### Post by wojox on 2010-06-21
Click the panel and install Indicator Applet.

---

### Post by amauk on 2010-06-21
Right click panel
Add to panel
Indicator Applet

---

### Post by wojox on 2010-06-21
You can reset the panels with these two command's


```

gconftool --recursive-unset /apps/panel
pkill gnome-panel


```

---

### Post by warfacegod on 2010-06-21
Being that your in Lucid, the only way to get rid of the Envelope icon is to remove Evolution. If you choose to do that, use Synaptic and be sure to read the other packages will be removed with each Evolution package. You could inadvertently remove things like gnomepanel-applets, if you aren't careful.

Edit: Actually removing the indicator-messages package will get rid of the icon.

---

### Post by seaders on 2010-07-07
> **wojox said:**
> You can reset the panels with these two command's


```

gconftool --recursive-unset /apps/panel
pkill gnome-panel


```

thanks so much for this!  after trying (and failing) to get one of two screens to rotate nicely in Twinview with the NVidia driver, my toolbars were all messed up and I had no real idea how to get 'em back to default ;)

thank you.

---

### Post by rosswmcgee on 2010-07-13
indicator-messages package removed// rebooted envelope icon still there// noted it This package provides a plugin for Evolution that uses libindicate and
libnotify to provide additional information about Evolution's state.

do I remove them too?

---

### Post by warfacegod on 2010-07-14
> **rosswmcgee said:**
> indicator-messages package removed// rebooted envelope icon still there// noted it This package provides a plugin for Evolution that uses libindicate and
libnotify to provide additional information about Evolution's state.

do I remove them too?

No. Removing indicator-messages is normally sufficient to remove the envelope. I don't know why it is still there.

---

### Post by anur.bhargav on 2010-08-28
:)

---

### Post by anur.bhargav on 2010-08-28
> **wojox said:**
> Click the panel and install Indicator Applet.

Thank you worked like a charm

---

