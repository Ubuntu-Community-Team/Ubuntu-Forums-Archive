---
title: "How do you un-install NVIDIA X Server Settings???????"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by lentomies on 2009-04-05
Hi!

I installed Envy NG which installed NVIDIA X Server Settings. Now I'd like to un-install NVIDIA X Server Settings...

How is this possible?

Thanks!

P.S. I un-installed ENVY NG using Synaptic but NVIDIA X Server Settings still remains...

---

### Post by asmoore82 on 2009-04-05
```
sudo apt-get remove nvidia-settings
```

If envy didn't install it on-the-side.

---

### Post by Kareeser on 2009-04-05
EnvyNG is only a delivery system and middleman program for installing the nvidia drivers. It's also open-source.

nvidia-settings is a proprietary program by nvidia :)

Just to make that clear.

---

### Post by lentomies on 2009-04-05
Thanks asmoore82 that did the trick!!!

---

