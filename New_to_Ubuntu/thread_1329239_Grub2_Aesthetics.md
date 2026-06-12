---
title: "Grub2 Aesthetics"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-11-17
Hi all,
I wanted to remove some of the entries, so I was left with either just Ubuntu and Windows, or that, but including recovery mode for Ubu.
Is this simple with Grub2? Any advice would be great :)
Robin

---

### Post by Paqman on 2009-11-17
Yep, pretty easy. To get rid of the memtest entry:
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

To remove excess Ubuntu entries, just uninstall those kernels. In Synaptic search for "linux-image" and remove all but the latest one.

Do you have any other entries you want to get rid of?

EDIT: You'll need to run 
```

sudo update-grub

```

...after making any changes to Grub config files, such as the memtest one above.

---

### Post by philinux on 2009-11-17
+1 paqman has it on the nose.

Click the grub2 link below for "more" info.

---

