---
title: "can't enable desktop effects"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by enri2 on 2009-03-22
i had  to power off  my pc , when it started  it said something like  ubuntu running in low graphics mode, then i reinstalled the graphics driver . NOw i can't enable desktop effects it says "desktop effects could not be enabled."

---

### Post by ibuclaw on 2009-03-22
Is the driver for your graphics card enabled in **Hardware Drivers**?

Goto:
System->Administration->Hardware Drivers.

In the Gnome menu.

Regards
Iain

---

### Post by enri2 on 2009-03-22
yes  it is enabled. I   can't  even play a video :(

---

### Post by jimv on 2009-03-22
What video card do you have?

---

### Post by canadiandude007 on 2009-03-24
I have NVIDIA accelerated graphics driver (version 96) enabled.  It says it is activated and currently in use, but I also get the same problem of enabling desktop effects.  It says I cannot.

---

### Post by canadiandude007 on 2009-03-24
My mistake, after I upgraded I had to reinstall compiz.

The compiz-settings-manager was there but not the compiz components, so I did a ...

```
sudo apt-get install compiz
```

which installed everything.

Then I went to System -> Preferences -> Appearance -> Visual Effects and clicked on "Normal".

I could then go to the compiz-settings-manager and enable various settings without a problem.

---

