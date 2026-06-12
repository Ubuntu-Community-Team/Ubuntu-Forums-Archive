---
title: "kill a process doesn't work"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by boojeboy on 2009-02-27
# pidof lircd

returns my process id, then I:
sudo kill [pid]

I ps -elf|grep lirc and it's still there!
# pidof lircd still there

I started another program that launches a window, I kill it and it goes away.
I've never seen a linux box that doesn't kill a process with: sudo kill [pid]

EDIT: now it works after exiting a terminal window. weird.

---

### Post by supersonicdarky on 2009-02-27
try **kill -9** (sends SIGKILL rather than default SIGTERM)

but if the process status is **D** (even worse **D<**), then there is no way to kill it and you will have to restart

---

### Post by jmszr on 2009-02-27
boojeboy,
           You might try System > Administration > System Monitor > Processes > click on the process of your choice > End Process

---

### Post by boojeboy on 2009-02-28
> **supersonicdarky said:**
> try **kill -9** (sends SIGKILL rather than default SIGTERM)

but if the process status is **D** (even worse **D<**), then there is no way to kill it and you will have to restart

wow, ok, thanks for the info!

---

