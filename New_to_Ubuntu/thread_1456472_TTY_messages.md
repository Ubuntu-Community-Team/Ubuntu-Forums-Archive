---
title: "TTY messages"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by new_tolinux on 2010-04-17
I installed 9.04 and added "text" to the bootline in grub. It boots to TTY1 (as it should) and there's no console-user.

But I'm just looking at the screen and I see about 5 times both "* Reloading Common Unix Printing System: cupsd" and "Reloading system log daemon...". It seems that those messages are produced about once a day.
Besides that I see a message "Starting anac(h)ronistic cron anacron, somewhere in the middle of the other messages.

Is this normal, or does that mean something is wrong.

---

### Post by dwarfolo on 2010-04-17
Yes it is. It's the log rotation system that stops/starts those services in order to archive the daily log in the /var/log directory.

---

### Post by new_tolinux on 2010-04-17
> **dwarfolo said:**
> Yes it is. It's the log rotation system that stops/starts those services in order to archive the daily log in the /var/log directory.
Thanks.

---

