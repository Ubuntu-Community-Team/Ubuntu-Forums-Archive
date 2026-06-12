---
title: "Gimp Won't boot"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-01-06
I had to reinstall Ubuntu 9.10 a little while ago, anyway, before I reinstalled it, Gimp would boot fine and worked perfectly except that fact that none of the drop down options allowed me to save a project as a jpeg. Anyway, now when click on Gimp, nothing happens and it never starts. I've reinstalled it 3 times. After this last install, I went to the terminal and typed Gimp and this was what it showed me


gimp: error while loading shared libraries: libgegl-0.1.so.0: cannot open shared object file: No such file or directory

---

### Post by themusicalduck on 2010-01-06
I had this same problem when I updated gimp to a newer version. If you search for libgegl in synaptic (System > Administration) and install libgegl-0.0-0 first. Then when I tried to run it, it reported another missing library (I can't remember which). If you search for it and install it in a similar way it should fix it.

I didn't get any more errors after that, but if it does tell you it needs more libs then you can probably find all of them in synaptic.

---

### Post by Bartender on 2010-01-06
Might be simpler to use Add/Remove to just uninstall GIMP, then reinstall from Synaptic?

---

### Post by sandyd on 2010-01-06
```

sudo dpkg --purge gimp libgegl-0.0-0
sudo apt-get install gimp libgegl-0.0-0

```
please use dpkg to purge gimp and gegl.
Otherwise, you will be removing a whole set of programs that depend on gimp and libgegl.

---

### Post by Captainflowers91 on 2010-01-06
> **carlee said:**
> ```

sudo dpkg --purge gimp libgegl-0.0-0
sudo apt-get install gimp libgegl-0.0-0

```please use dpkg to purge gimp and gegl.
Otherwise, you will be removing a whole set of programs that depend on gimp and libgegl.

Worked like a charm, Gimp booted right after I ran the second prompt, didn't even have to reboot my computer. thank you!

---

### Post by juancarlospaco on 2010-01-06
*Gimp dont boot...*
:)

---

### Post by perevera on 2010-04-18
> **Captainflowers91 said:**
> Worked like a charm, Gimp booted right after I ran the second prompt, didn't even have to reboot my computer. thank you!

This worked for me as well! Thanks, carlee!

---

### Post by Praxi on 2012-04-05
My Gimp 2.6 was broken also, mainly because I was trying to install one of the beta versions of gimp.

This thread helped, but I had to do one additional package.  And sorry for the thread Necro, but its the first google hit that came up.

```
sudo dpkg --purge gimp libgegl-0.0-0
sudo dpkg --purge gimp libbabl-0.0-0 
sudo apt-get install gimp libgegl-0.0-0
sudo apt-get install gimp libbabl-0.0
```

---

