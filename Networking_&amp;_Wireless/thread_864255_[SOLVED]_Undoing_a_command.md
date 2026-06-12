---
title: "[SOLVED] Undoing a command"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by daggerx on 2008-07-19
I did this command and realized that I didn't need it, so now my question is how do I undo it:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

```

I just got a T41 and I have a usb wifi card for it and it is using the prismusb driver. I realized that I do not need to do the blacklisting stuff (I believe) since the card works outside the box.

---

### Post by sisco311 on 2008-07-19
open the file in the text editor
and delete the last line (*blacklist bcm43xx*):

```
gksu gedit /etc/modprobe.d/blacklist
```

---

### Post by daggerx on 2008-07-19
OK, done, thank you. Why does it say this:

```
# replaced by p54pci
blacklist prism54
```

Should I be concerned about that?

---

### Post by sisco311 on 2008-07-19
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```= add *blacklist bcm43xx *to the end of the */etc/modprobe.d/blacklist *file.

In Hardy the bcm43xx module is blacklisted by default.
So the command was redundant and harmless.

---

### Post by daggerx on 2008-07-19
ok cool, got it

---

