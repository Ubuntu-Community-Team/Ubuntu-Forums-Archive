---
title: "trouble installing envy"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by marenum on 2009-05-20
I'm trying to install envy because I can't get the Nvidia driver to work. When I install envy it doesn't show up anywhere. I'm not sure what I'm doing wrong. I followed these directions:

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

---

### Post by sandyd on 2009-05-20
GO to Applications -> Accessories  -> Terminal
type in

```

envyng -t

```

follow onscreen instructions

---

### Post by fooman on 2009-05-20
look in applications > system tools

---

### Post by marenum on 2009-05-20
> **carlee said:**
> GO to Applications -> Accessories  -> Terminal
type in

```

envyng -t

```

follow onscreen instructions

When I do this i get:
"/usr/bin/envyng: line 6: cd: /usr/share/envy: No such file or directory
python: can't open file 'interface.py': [Errno 2] No such file or directory"

---

### Post by marenum on 2009-05-20
and it doesn't show up in applications > system tools.

---

### Post by damis648 on 2009-05-20
Do you require the use of envy? Have you tried System>Administration>Hardware Drivers?

---

### Post by marenum on 2009-05-20
> **damis648 said:**
> Do you require the use of envy? Have you tried System>Administration>Hardware Drivers?

When I do it from there, When I restart I get this message:

"Ubuntu is running in low graphics mode.

The following error was encountered. You may need to upgrade your configuration to fix this.

(EE) NVIDIA (0) failed to load the NVIDIA kernel module!
(EE) NVIDIA (0) ***aborting***
(EE) Screens (s) found, but none have usuable configuration"

I'm very confused, this started happening after I updated to 9.04. This driver worked fine before the update.

---

