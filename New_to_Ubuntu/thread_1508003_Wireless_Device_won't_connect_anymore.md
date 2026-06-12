---
title: "Wireless Device won't connect anymore"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by [V] on 2010-06-12
I am running Lucid Lynx with a WG311v2 PCI Card.

I installed it with Ndiswrappers and it was running fine. Upon a reboot, the drivers did not load automatically. I was slightly disgruntled as I opened the shell and typed:

# depmod -a
# modprobe ndiswrapper

At this point it reconnected & I began to download software updates.
I came back the next morning and I was disconnected & it was asking me for my network password.

Now everytime I try and connect, it just tries to connect for like 30 seconds then prompts me for my password again. My password is in fact correct. Even after multiple reboots.

Whats going on here?

Thanks.

-V

---

### Post by sadaruwan12 on 2010-06-12
I also have the same kind of a problem with my RTL8187b wireless card what I do when I get disconnected just remove the drivers restart install it back the shutdown the laptop for few minuets then start it back up.

After that I get connected.

---

### Post by SlidingHorn on 2010-06-12
Hey guys...I'm not sure if this is the exact same issue, but give this thread a look: [http://ubuntuforums.org/showthread.php?t=1466181](http://ubuntuforums.org/showthread.php?t=1466181)

---

### Post by llawwehttam on 2010-06-12
Try ```
sudo apt-get install linux-backports-modules-2.6.31-14-generic && sudo reboot
```

if it doesn't work replace 2.6.31-14-generic with the output of the command ```
uname -r
```

works for some.

---

