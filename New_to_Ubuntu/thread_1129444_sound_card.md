---
title: "sound card"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Jatchie on 2009-04-18
I just bought a new sound card ,and installed it

sudo asoundconf list
ICE1724
Default 
I dont't know how to install the drivers can anyone help me.
sudo asoundconf set-default-card-ICE1724
 I did that command and I still have no sound :(

---

### Post by Jatchie on 2009-04-18
?

---

### Post by Jatchie on 2009-04-18
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

---

### Post by halitech on 2009-04-18
did you try running ```
sudo alsaconf
``` to see if it can detect the new sound card?

---

### Post by Jatchie on 2009-04-18
```
 sudo alsaconf

``` yeah 
and I tried ```
 sudo -i

``````
alsaconf

```-bash: alsaconf: command not found

---

### Post by halitech on 2009-04-19
is alsa installed?

---

### Post by Jatchie on 2009-04-19
yeah

---

