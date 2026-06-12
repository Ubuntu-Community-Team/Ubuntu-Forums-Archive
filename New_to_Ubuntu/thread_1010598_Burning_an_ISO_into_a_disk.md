---
title: "Burning an ISO into a disk"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-13
just downloaded openSUSE 11.0 onto my ubuntu pc and wanting to burn the ISO to a CD... how would i go about burning the ISO?

i tried rightclick and did a write to disc but i think it was written to it as data...

---

### Post by dchglat on 2008-12-13
> **manuleka said:**
> just downloaded openSUSE 11.0 onto my ubuntu pc and wanting to burn the ISO to a CD... how would i go about burning the ISO?

i tried rightclick and did a write to disc but i think it was written to it as data...
download a program called K3b from synaptic package manager. It will provide you with the option to burn an ISO onto a cd.

---

### Post by EdThaSlayer on 2008-12-13
> **manuleka said:**
> just downloaded openSUSE 11.0 onto my ubuntu pc and wanting to burn the ISO to a CD... how would i go about burning the ISO?

i tried rightclick and did a write to disc but i think it was written to it as data...

Since my guess is that you use GNOME, you might want to try
> gnomebaker - application for CD/DVD creation in the GNOME desktop

You should be able to find it in the repositories.

---

### Post by Hydrid on 2008-12-14
Go to Applications ---> Sound&Video ---> Brasero Disc Burning (Click to run it)and you will see an option [ Burn Image ].

If this helped you click on solved so it can help others too and thanks on the right right corner of the post.It would be appriciated :)

---

### Post by manuleka on 2008-12-14
yip managed to use the Brasero Disc Burning tool :) thanks guys

---

### Post by dwasifar on 2008-12-14
I know you solved your problem already, but here's another option - burning from the commandline:

```
growisofs -Z /dev/dvd {filename}
```

If you don't have /dev/dvd as a device, /dev/cdrom usually works too.

---

