---
title: "How to disable wlan card."
date: 2010-10-11
forum: New to Ubuntu
---

### Post by krikett on 2010-10-11
[COLOR=#000000]I have Ubuntu 10.10, which included the driver for the alpha awus036h with. [/COLOR]It is now the problem is that both network cards running at the same time. [COLOR=#000000]So I just disable the integrated card. [/COLOR]How do I do that?

---

### Post by robsoles on 2010-10-18
Have you looked in the BIOS of this machine (usually [F2] or [Del]/[Delete] while computer is starting up after power-on) for settings related to built-in peripherals.

If you can disable it there is best, post back whether you can or can't do it there.

---

### Post by MooPi on 2010-10-18
How about: ```
ifdown wlan0
```
Short and sweet.

---

### Post by robsoles on 2010-10-18
> **MooPi said:**
> How about: ```
ifdown wlan0
```
Short and sweet.

Does that persist? (Will it stay 'down' through  a restart?)

---

### Post by uRock on 2010-10-18
> **robsoles said:**
> Does that persist? (Will it stay 'down' through  a restart?)
A batch file can be created and set to run in Startup Applications.

---

