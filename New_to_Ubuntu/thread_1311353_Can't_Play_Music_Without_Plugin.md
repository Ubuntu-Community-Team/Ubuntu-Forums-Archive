---
title: "Can't Play Music Without Plugin"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by BlazeFire247 on 2009-11-02
I couldn't play music on either Totem or Rhythmbox because it needed a plugin (MPEG-1 Layer 3 (MP3) decoder). It then finds a plugin then it says "No packages with the requested plugins found". They worked in 9.04, how do I get it for 9.10?

---

### Post by meho_r on 2009-11-02
ubuntu-restricted-extras

---

### Post by Temposs on 2009-11-02
You should install the "Ubuntu Restricted Extras" package. Search for it in the Ubuntu Software Center.

---

### Post by superharas on 2009-11-02
Or download it from here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by BlazeFire247 on 2009-11-02
> **Temposs said:**
> You should install the "Ubuntu Restricted Extras" package. Search for it in the Ubuntu Software Center.

I tried doing that, but it said that it's not available in the current data.

---

### Post by meho_r on 2009-11-02
Check your repos. System > Administration > Software Sources. Be sure that first 4 boxes are ticked. Open Synaptic (System > Administration > Synaptic...), press "Reload", and then search for word *restricted*.

---

### Post by heyho on 2009-11-02
What if you try the following?

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by BlazeFire247 on 2009-11-02
> **meho_r said:**
> Check your repos. System > Administration > Software Sources. Be sure that first 4 boxes are ticked. Open Synaptic (System > Administration > Synaptic...), press "Reload", and then search for word *restricted*.

Thank you! And thanks for those who helped, too :D

---

