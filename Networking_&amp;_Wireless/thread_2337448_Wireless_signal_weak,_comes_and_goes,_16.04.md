---
title: "Wireless signal weak, comes and goes, 16.04"
date: 2016-09-18
forum: Networking &amp; Wireless
---

### Post by tpedersen6 on 2016-09-18
In windows I don't have any issues but when I boot into Ubuntu 16.04 my wireless signal is weak and come and goes, I also get intermittent screen flicker.  Rather than the wireless radio at the top I always see the wired network icon if that means anything.

---

### Post by Bucky Ball on 2016-09-18
> **tpedersen6 said:**
> Rather than the wireless radio at the top I always see the wired network icon if that means anything.

It could mean that you have an ethernet cable plugged in and it is overriding the wireless. It always will so if this is the case, unplug the ethernet, reboot with ethernet out and see if that works.

If it doesn't, please open a terminal and post the output of this command *between code tags*. (See link in my signature for how.)

```
sudo lshw -C network
```

PS: I have taken the liberty of changing your thread title to something that reflects you actual problem. Feel free to change to something else again by editing first post and 'Go Advanced'. You have a better chance of support with a non-generic, descriptive thread title. Could you please add the machine (Spectre something?) to the body of your first post? :)

---

