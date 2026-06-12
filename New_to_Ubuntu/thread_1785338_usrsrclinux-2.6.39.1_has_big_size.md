---
title: "/usr/src/linux-2.6.39.1 has big size ??"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by madesyu on 2011-06-18
hello , i just compile linux kernel 2.6.39.1 :)

just wanted to ask everyone here. my /usr/src/linux-2.6.39.1
after compiling has approximately 420 MB is it normal ?? 

whereas my linux-2.6.38 headers and linux-2.6.38-generic , both of them only has approximately 70 MB

and one more thing , is it safe to deleted /usr/src/linux-2.6.39.1 ??

---

### Post by amauk on 2011-06-18
Most likely you've compiled the kernel with debugging symbols

In the menuconfig, goto
Kernel hacking > Kernel debugging
and uncheck "Compile the kernel with debug info"

File size will now be much smaller

*edit*
Btw, kernel compiling is hardly a topic for "absolute beginners", but hey...

---

### Post by madesyu on 2011-06-18
after edit menuconfig , should i recompile ?
or i just need to save the configuration

---

### Post by amauk on 2011-06-18
> **madesyu said:**
> after edit menuconfig , should i recompile ?
or i just need to save the configurationYou'll need to recompile

---

### Post by madesyu on 2011-06-18
ok, thanks for the answer i`ll recompile it , and report it later

---

### Post by madesyu on 2011-06-19
great !!! it`s work , now my /usr/src/linux-2.6.39.1 approximately has only 190 MB. thanks amauk:KS

---

### Post by dFlyer on 2011-06-19
Please mark SOLVED.

---

