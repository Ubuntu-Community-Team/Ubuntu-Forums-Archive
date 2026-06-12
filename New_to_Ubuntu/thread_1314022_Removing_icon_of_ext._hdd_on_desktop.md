---
title: "Removing icon of ext. hdd on desktop"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Cruvenium on 2009-11-04
I have a icon of my external HDD on my desktop when it is plugged in.

Are there anyways to remove that icon? I Googled but there's nothing relevant..

I cannot move it to trash. This is what happens when I try to delete it.

[IMG]http://a.imagehost.org/0225/Screenshot-1.png[/IMG]

---

### Post by phillw on 2009-11-04
> **Cruvenium said:**
> I have a icon of my external HDD on my desktop when it is plugged in.

Are there anyways to remove that icon? I Googled but there's nothing relevant..

I cannot move it to trash. This is what happens when I try to delete it.

[IMG]http://a.imagehost.org/0225/Screenshot-1.png[/IMG]

You can tell it not to auto-mount, but you'd lose access to the device. By default, when a device (hard-drive, cd, usb device etc) is 'found' and mounted by ubuntu, it 'tells' you it has succeeded by popping an icon on your desktop.

Phill.

---

### Post by Cruvenium on 2009-11-04
So in other words I cannot remove that icon?

---

### Post by happyhamster on 2009-11-04
- In a terminal (Applications-->Accessories-->Terminal), type:

gconf-editor

- Search for apps-->nautilus-->desktop and untick the "volumes_visible" option. Mind you, this will prevent *any* volumes from being shown. Good luck.

---

### Post by Cruvenium on 2009-11-04
By any volumes, you mean other drives/thumbdrives plugged in?

Will they be shown under Places though?

---

### Post by nothingspecial on 2009-11-04
> **Cruvenium said:**
> By any volumes, you mean other drives/thumbdrives plugged in?

Will they be shown under Places though?

Exactly

---

### Post by happyhamster on 2009-11-04
> **Cruvenium said:**
> By any volumes, you mean other drives/thumbdrives plugged in?
Yes.

> 
Will they be shown under Places though?
Yes, no problem.

---

### Post by Cruvenium on 2009-11-04
Alright, thank you :)

---

### Post by cmcanulty on 2009-11-04
Get Ubuntu tweak
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)
go to desktop tab and uncheck "show mounted volumes on desktop"
lots of other user tweaks too, I love it

---

