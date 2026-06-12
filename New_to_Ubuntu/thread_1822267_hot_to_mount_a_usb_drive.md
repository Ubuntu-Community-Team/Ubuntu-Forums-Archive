---
title: "hot to mount a usb drive ??"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by squrl on 2011-08-10
xxx

---

### Post by sanderd17 on 2011-08-10
The mount command will mount a drive to a location specified in the fstab or the mtab file, or to a location you provide. Since you don give a location and the fstab and the mtab file don't have a location, it can't be mounted. You should add the location to your mount command:

```

mount /dev/sde /backup

```

---

### Post by squrl on 2011-08-10
xxx

---

### Post by sanderd17 on 2011-08-10
Hmmm, never had this before, so I went googling.

One of the answers suggested adding -o nolock to the command:

```

mount /dev/sde /backup -o nolock

```

But I really don't know it myself. It's worth trying.

---

### Post by squrl on 2011-08-10
xxx

---

### Post by sanderd17 on 2011-08-10
Sorry, I can't help you further. I never encountered it, so googling was the only thing I could do.

---

