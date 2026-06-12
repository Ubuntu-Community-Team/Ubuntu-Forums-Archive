---
title: "Ubuntu is not coming up!"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by aminj on 2009-06-30
Hi,

It is a while I'm using Ubuntu (as you know, it does not mean I'm an expert!!) Yesterday I installed a couple of packages and then restart the computer and Ubuntu never comes up again! In the system checking part before initiating the graphical part every thing is [OK], once the graphic part starts it shows some vertical colored lines and then HANG! you can not press any key or move the curser. nothing! I can go to the recovery. I tried to fix the problem there but I did not have any idea how! Can someone please help me NOWW? :(

THANKS,
Amin

---

### Post by Paqman on 2009-06-30
What exactly did you install?

Can you boot up into recovery mode and uninstall the things you installed? Use:
```

apt-get remove packagename

```

from the root shell prompt that you'll get in recovery mode.

---

### Post by aminj on 2009-06-30
The problem is I installed like 100 packages that I do not even remember what they was! is there anyway to somehow clean up the graphical booting configuration?

---

### Post by Paqman on 2009-06-30
> **aminj said:**
> The problem is I installed like 100 packages that I do not even remember what they was! is there anyway to somehow clean up the graphical booting configuration?

Without knowing what changes you made, it's pretty hard to recommend an effective solution.

You could try:
```

xfix

```
from the recovery mode, but it's a bit of a stab in the dark.

---

### Post by aminj on 2009-06-30
I tried it. It didn't work! :(

---

### Post by Tyke91 on 2009-06-30
hm

try typing ```
xorgconfig
``` and answering the questions that come up. Make sure to tell it to save to /etc/X11/xorg.conf 

if it doesn't save there by default, rememeber where it DID save, then type in the terminal ```
mv /location/of/the/file/and/its/name /etc/X11/xorg.conf
```
other than that, we can't help you unless you give us more information.

---

