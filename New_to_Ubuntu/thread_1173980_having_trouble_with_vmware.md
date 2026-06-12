---
title: "having trouble with vmware"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-05-30
trying to install xp in vmware and am having a few problems.  first off i tried vmware server which i didn't like so now am trying to install in vmware player. first thing i would like to know is where my vmware server virtual harddisk is stored so i can delete it and get some space back on my hd?  next how do i create a vm to run in vmware player?

---

### Post by billgoldberg on 2009-05-30
> **mamamia88 said:**
> trying to install xp in vmware and am having a few problems.  first off i tried vmware server which i didn't like so now am trying to install in vmware player. first thing i would like to know is where my vmware server virtual harddisk is stored so i can delete it and get some space back on my hd?  next how do i create a vm to run in vmware player?

The documentation on the vmware website will be able to tell you these things, but I would advise you use Virtualbox instead.

Much easier to use, and completely free.

---

### Post by mamamia88 on 2009-05-30
> **billgoldberg said:**
> The documentation on the vmware website will be able to tell you these things, but I would advise you use Virtualbox instead.

Much easier to use, and completely free.

yeah but what i wanted to do in virtualbox doesn't work

---

### Post by mamamia88 on 2009-05-30
does anyone have an idea where harddisk might be stored in filesytem?  i want my 25gb back and have been digging through filesystem trying to find the virtual disc please help me out here

---

### Post by JohnLeoZ on 2009-06-03
> **mamamia88 said:**
> does anyone have an idea where harddisk might be stored in filesytem?

Look for the extension .vmdk which will be on all the virtual drive files.
There will also always be a "vmware.log" file in the same folder.

jlz

---

### Post by graphius on 2009-06-03
also note it may be a hidden folder. in nautilus press crtl+h

---

### Post by nandemonai on 2009-06-03
> **mamamia88 said:**
> does anyone have an idea where harddisk might be stored in filesytem?  i want my 25gb back and have been digging through filesystem trying to find the virtual disc please help me out here

VMware Server? /var/lib/vmware/Virtual\ Machines/

---

