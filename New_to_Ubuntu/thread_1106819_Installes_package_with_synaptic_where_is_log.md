---
title: "Installes package with synaptic where is log"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by markotitel on 2009-03-26
Hi, how can I see install messages after closing synaptic. For example, i installed amanda and that instalation created user backup and group backup. That is shown while installing package, how can I find these messages again?

---

### Post by taavikko on 2009-03-26
Menu->System->Admin->Log file viewer -->>> dpkg.log
Is what you're after?

Synaptic has an "history" menu entry that provides roughly the same thing.

Every log is located in /var/log/ folder.

---

### Post by markotitel on 2009-03-26
Hi,
Im familiar with dpkg log, but there I cannot see messages that are displayed during install process, AMANDA instalation creates user BACKUP group BACKUP I saw that while installing amanda using synaptic, but where do I find these install messages after?

---

### Post by taavikko on 2009-03-26
> **markotitel said:**
> Hi,
Im familiar with dpkg log, but there I cannot see messages that are displayed during install process, AMANDA instalation creates user BACKUP group BACKUP I saw that while installing amanda using synaptic, but where do I find these install messages after?

Like I said, almost every log can be found in /var/log/
Viewable via System->Admin->Log file viewer

There you can search the messages

Probably "messages" or "auth.log" is the correct one.

Or you can search via "grep" in CLI

```
grep -i amanda /var/log/
```
But you must alter the search word to find the correct lines you're seeking.

I haven't installed this particular app, so can't know for sure.

---

