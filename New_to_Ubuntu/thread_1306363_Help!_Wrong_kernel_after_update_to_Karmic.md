---
title: "Help! Wrong kernel after update to Karmic"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by camaron1 on 2009-10-30
I've just updated to Karmic and after instalation I have karmik with kernel 2.28. So far I've just discover that I lost all sound.

Help with this please

---

### Post by camaron1 on 2009-10-30
Sorry I sent it twice

---

### Post by cariboo on 2009-10-30
Can you not choose what kernel to boot from in the grub menu? You install the latest kernel by going to System-->Administration--<\>Synaptic Package Manager, and search for:

```
linux-image
```

That should install the latest kernel which is:

```
2.6.31-14-generic #48-Ubuntu SMP
```

---

### Post by cariboo on 2009-10-30
Please don't double post, I have merged your two threads

---

### Post by camaron1 on 2009-10-30
> **cariboo907 said:**
> Can you not choose what kernel to boot from in the grub menu? You install the latest kernel by going to System-->Administration--<\>Synaptic Package Manager, and search for:

```
linux-image
```

That should install the latest kernel which is:

```
2.6.31-14-generic #48-Ubuntu SMP
```

The startup manager tells me that the version installad is 2.6.28 and the 2.6.31 does not appear. According to Synaptic the linux image of 2.6.31 is intalled

??

---

### Post by camaron1 on 2009-10-30
See attachment to see what grub's configuration file says

---

