---
title: "[Artful] where changing MTU ?"
date: 2017-12-05
forum: Networking &amp; Wireless
---

### Post by dino99 on 2017-12-05
I'm searching how to change the default MTU (576 here), set by a fresh install, with a fully working (tested) 1472 value.
The gnome 3.26 interface is now completely new, and the network settings are hidden somewhere.

If you can share your experience, i will be thanks full .

---

### Post by powersj on 2017-12-05
Settings -> Network -> Gear Icon next to the interface you wish to modify -> Identity -> MTU

---

### Post by dino99 on 2017-12-05
> **powersj said:**
> Settings -> Network -> Gear Icon next to the interface you wish to modify -> Identity -> MTU

Thanks for the answer, but the gnome 3.26.2 Settings -> Network have changed: now its only about vpn , there is no gear to do change; Tested also via dconf, but have not found MTU.

---

### Post by powersj on 2017-12-05
Interesting, my About shows me running "GNOME 3.26.2" as well. Here is what my network tab shows: [https://imgur.com/a/GJ064](https://imgur.com/a/GJ064)


I take it yours is missing the top half for "wired"?

---

### Post by dino99 on 2017-12-05
> **powersj said:**
> Interesting, my About shows me running "GNOME 3.26.2" as well. Here is what my network tab shows: [https://imgur.com/a/GJ064](https://imgur.com/a/GJ064)


I take it yours is missing the top half for "wired"?

You are right, this is missing on mine.
I wonder if it can be related to the affected name 'logical name: enp2s0' from 'sudo lshw -class network' command ; which is different from the usual ethX name.
This is from an asrock mobo chipset r8168e

Do you remember which package provide that 'Settings' menus ?

---

### Post by powersj on 2017-12-05
> **dino99 said:**
> 
I wonder if it can be related to the affected name 'logical name: enp2s0' from 'sudo lshw -class network' command ; which is different from the usual ethX name.
This is from an asrock mobo chipset r8168e


My lshw shows "logical name: enp3s0" so I don't think persistent network naming is causing this.

> **dino99 said:**
> 
Do you remember which package provide that 'Settings' menus ?

gnome-control-center

```

$ dpkg -S /usr/bin/gnome-control-center 
gnome-control-center: /usr/bin/gnome-control-center
```

---

