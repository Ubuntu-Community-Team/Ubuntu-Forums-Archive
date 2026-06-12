---
title: "Prevent natty upgrade pop up"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by gredawarha on 2011-06-10
Hello all

I have 10.04 Kubuntu installed on my mothers machine, however it regularly pops up notifying that 11.04 is available.  I want her to stay on LTS, can I disable this and future upgrade notifications?

Appreciate any help

---

### Post by imasickboy on 2011-06-10
Synaptic/Repositories/Updates

Change the dropdown box at the bottom. :)

Edit: Nevermind. Obviously I didn't read properly. There's a K in front of that-there ubuntu.

---

### Post by el_koraco on 2011-06-10
> **gredawarha said:**
> Hello all

I have 10.04 Kubuntu installed on my mothers machine, however it regularly pops up notifying that 11.04 is available.  I want her to stay on LTS, can I disable this and future upgrade notifications?

Appreciate any help

Go to KpackageKit, then updates, "Edit origins (sources?)", (or you ca just hit ALT + F2 and input 

```
kdesudo software-properties-kde

```
Then you need to go to the "Updates" tab, look under "Notify about releases", and select either "Never" or "Only LTS" from the menu.

---

### Post by gredawarha on 2011-06-10
I dint think Kubuntu had synaptic?

---

### Post by gredawarha on 2011-06-10
Thanks el_koraco managed to find that using your help

Thanks again

---

### Post by el_koraco on 2011-06-10
Sure, don't forget to mark the thread as solved.

---

