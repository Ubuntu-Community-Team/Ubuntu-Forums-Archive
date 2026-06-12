---
title: "What driver am I using?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Duskao on 2009-04-27
Is there a command or a way to tell what graphic/video card driver I am actually using in Ubuntu 9.04?

---

### Post by Paddy Landau on 2009-04-27
I'm not entirely sure. Try this in terminal (Accessories -> Terminal).
```
sudo lshw -C video
```

---

### Post by Duskao on 2009-04-27
Well, that told me about the hardware I am using, but I didn't notice anything about any drivers. But lots of info on the video hardware :)

---

### Post by Didius Falco on 2009-04-27
try ```
dmesg | grep -i nvidia
``` or ati, if that's what kind of card you have. The -i tells it to ignore the case of the word.

I hope it helps...

---

### Post by Duskao on 2009-04-27
Well, I know that I am using an Ati video card so would that command have any bearing on my system? can I switch the "nvidia" for "ati" and have it work?

---

### Post by Didius Falco on 2009-04-27
yes, just use ati instead of nvidia.

---

