---
title: "Two Moniters"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by leinad177 on 2010-03-10
i have 2 moniters and i set them up to work..

but as soon as i restart my computer i have to redo it or i can only use one screen

is there any way to make my changes stay?

---

### Post by wojox on 2010-03-10
What video card/chip?

```
lspci | grep VGA
```

---

### Post by leinad177 on 2010-03-10
> **wojox said:**
> What video card/chip?

```
lspci | grep VGA
```

Nvidia GTX 260

and thanks for the code :P

---

### Post by wojox on 2010-03-10
Okay firstly run:

```
sudo nvidia-xconfig
```

Then:

```
sudo nvidia-settings
```

This will give you root privilege's to set your xorg.conf file and make it persistent (stick after you reboot).

---

### Post by leinad177 on 2010-03-10
> root@daniel-desktop:/home/daniel# sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
this is what came up

---

### Post by wojox on 2010-03-10
Okay, you really shouldn't be running as root. Exit out of root and run those commands again. That's what you want to see is that it New X configuration file written to '/etc/X11/xorg.conf'

Then you just need to open up nvidia-settings like above:

```
gksudo nvidia-settings
```

---

### Post by leinad177 on 2010-03-10
ok...so im not meant to put those commands in the root terminal?

if not, then where?

---

### Post by wojox on 2010-03-10
Just go to Applications > Accessories > Terminal ;)

---

### Post by leinad177 on 2010-03-10
Thanks!

It works now :P

---

