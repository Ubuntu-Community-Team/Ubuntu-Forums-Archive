---
title: "share folder w/o nautilus"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by dbbolton on 2007-05-31
whenever i wanted to share a folder between two ubuntu machines, i always just right-clicked the folder, then clicked "share" in order to share it through samba.

how do you do this without nautilus? (i'm using thunar)

---

### Post by merlinus on 2007-05-31
system/administration/shared folders.

hth....

-merlin

---

### Post by dbbolton on 2007-05-31
> **merlinus said:**
> system/administration/shared folders.

hth....

-merlin
i also don't have gnome-panels. i'm using openbox.

---

### Post by ryanVickers on 2007-05-31
Oh, that's a problem :)

I would just use nautilus because thunar and dolphin and those aren't really fully functional (at least not as much as nautilus, and it integrates with gnome better).

---

### Post by dbbolton on 2007-05-31
> **ryanVickers said:**
> Oh, that's a problem :)

I would just use nautilus because thunar and dolphin and those aren't really fully functional (at least not as much as nautilus, and it integrates with gnome better).
yeah, but you can't use all the features of openbox with nautilus. for instance, when you right click on the desktop on openbox, you get the openbox menu. in nautilus, you get a context menu such as "change background, new launcher" etc. if you use them both, nautilus covers up openbox, and you can't use the openbox menu.

---

### Post by dbbolton on 2007-06-01
all right, i think i got it.

```
gksudo shares-admin
```

(thanks, deskbar)

---

### Post by airtonix on 2007-06-22
you can prevent nautlius from becoming the desktop.....

it takes over the desktop.

To prevent this find out where it is being told to load at startup and change the 

> nautilusto 

> nautilus --no-desktopyou can now access the openbox desktop that was always there, but covered by nautilus.

or you could add the item element shown here 

> <menu id="root-menu">
  ...
  <item label="samba-share admin">
    <action name="Execute"><execute>gksudo shares-admin</execute></action>
  </item>
  ...
</menu>to your 

> ~/.config/openbox/menu.xml

---

