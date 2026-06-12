---
title: "Whats the best way to view partition?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by casmok on 2009-03-03
Whats the best way to view my partition and the "Real" amount of used vs free space? 

From what I can see there are two options:
1.Applications>Accesories>disk-usage-analyser which is a bit simple and crude or, 
2. right click on "File System" and select "properties" which give a numerical breakdown.

The exact figures vary slightly between the two methods as well :confused: 

Is there a better utility available?

---

### Post by linuxuser21 on 2009-03-03
I use Gparted.

---

### Post by taurus on 2009-03-03
Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by casmok on 2009-03-03
> **taurus said:**
> Applications -> Accessories -> Terminal
```
df -h
```

Thanks. The terminal command works pretty slick. Curious what are the ther values below? eg varrun, varlock, udev, lrm and ile ?

Also curious is there a graphical tool available/download to do this as well?

I could use gparted but for that I need the instlation disk dont I?

---

### Post by kevin11951 on 2009-03-03
> **casmok said:**
> Thanks. The terminal command works pretty slick. Curious what are the ther values below? eg varrun, varlock, udev, lrm and ile ?

Also curious is there a graphical tool available/download to do this as well?

I could use gparted but for that I need the instlation disk dont I?

gparted will tell you about your hdd as well as partition it if you tell it to.

---

### Post by oldos2er on 2009-03-03
"I could use gparted but for that I need the instlation disk dont I?"

 You can install it from Add/Remove or Synaptic Package Manager.

---

### Post by casmok on 2009-03-03
[QUOTE=oldos2er;6833261]"I could use gparted but for that I need the instlation disk dont I?"

 You can install it from Add/Remove or Synaptic Package Manager.[/QUOTE

Thanks. I'm not at home right now which is why I dont have the disk.

I'd mark this as solved but that option seems to have disapeared!

Mike

---

