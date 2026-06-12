---
title: "my wireless card has stopped working"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by kalimojo on 2011-07-18
im on ubuntu 11.04
i have a ralink wifi card builtin

i had it working for several months after installing the drivers for it. now it doesnt show up in iwconfig anymore.

any ideas ?

---

### Post by gandaran on 2011-07-18
> **kalimojo said:**
> im on ubuntu 11.04
i have a ralink wifi card builtin

i had it working for several months after installing the drivers for it. now it doesnt show up in iwconfig anymore.

any ideas ?
if you installed a kernel update then you will have to re-install the drivers again.

---

### Post by kalimojo on 2011-07-18
> **gandaran said:**
> if you installed a kernel update then you will have to re-install the drivers again.
yes the update program updated the kernel im sure. PITA.

---

### Post by amjjawad on 2011-07-18
> **kalimojo said:**
> im on ubuntu 11.04
i have a ralink wifi card builtin

i had it working for several months after installing the drivers for it. now it doesnt show up in iwconfig anymore.

any ideas ?

Hi,

Please post back the output of:

```
sudo lshw -C network

```

Please wrap up the text that you'll post here with "#" at the beginning and at the end.

Thank you :)

---

### Post by kalimojo on 2011-07-18
I reinstalled the drivers and its now ok. thanks to gandaran for the tip

---

### Post by amjjawad on 2011-07-18
> **kalimojo said:**
> I reinstalled the drivers and its now ok.

Glad you managed to fix it :)
Good job!

---

