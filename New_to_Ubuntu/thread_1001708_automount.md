---
title: "automount"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by uttaran on 2008-12-04
How to prevent automounting of cds and pen drives in Gutsy???

---

### Post by Dedoimedo on 2008-12-04
You can remove the corresponding entry in the /etc/fstab file.
Please note that mis-configuring this file can cause your hard drives not to be mounted.

Therefore:

1. Backup first!
```
sudo cp /etc/fstab /etc/fstab-backup
```

2. Open the file in a text editor:

```
sudo gedit /etc/fstab
```

Only COMMENT the cd-rom/usb line in the file. Then run the following command to take effect:

```
sudo mount -a
```

Reinsert CD/USB to test ...

Ask if you need more help. Post the contents of your fstab here if you need a second opinion, consultation etc.

Cheers,
Dedoimedo

---

### Post by billgoldberg on 2008-12-04
> **Dedoimedo said:**
> You can remove the corresponding entry in the /etc/fstab file.
Please note that mis-configuring this file can cause your hard drives not to be mounted.

Therefore:

1. Backup first!
```
sudo cp /etc/fstab /etc/fstab-backup
```

2. Open the file in a text editor:

```
sudo gedit /etc/fstab
```

Only COMMENT the cd-rom/usb line in the file. Then run the following command to take effect:

```
sudo mount -a
```

Reinsert CD/USB to test ...

Ask if you need more help. Post the contents of your fstab here if you need a second opinion, consultation etc.

Cheers,
Dedoimedo

That's a bit overkill.

Just press "alt+f2" and enter "gconf-editor".

Then in the apps -> nautilus > preferences. Disable the "media_automount" feature.

Done.

--

Edit: I see you say Gutsy

I don't remember if nautilus mounted the drives in Gutsy, if it doesn't try this: press "alt+f2" and enter "gnome-volume-properties" and disable the "mount removable".

Done.

---

### Post by Dedoimedo on 2008-12-04
Give a man fire; and he'll be warm for the rest of the day.
Set a man on fire; and he'll be warm for the rest of his life.

Using /etc/fstab is an overkill, but it works anytime, everywhere, regardless of what GUI you may be or may not be using.

Dedoimedo

---

### Post by Paqman on 2008-12-04
> **Dedoimedo said:**
> 
Using /etc/fstab is an overkill, but it works anytime, everywhere, regardless of what GUI you may be or may not be using.


Sure, but this is the Absolute Beginners section. We strongly encourage supplying GUI-based answers unless the OP is specifically asking for CLI instructions.

---

### Post by maandverband on 2008-12-04
> **Dedoimedo said:**
> 2. Open the file in a text editor:

```
sudo gedit /etc/fstab
```

CLI-apps: use sudo:

```
sudo nano /etc/fstab
```

Graphical apps in GNOME: use gksu:

```
gksu gedit /etc/fstab
```

Graphical apps in KDE: use kdesu:

```
kdesu kate /etc/fstab
```

---

