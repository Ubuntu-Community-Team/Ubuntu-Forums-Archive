---
title: "Ubuntu won't load up after update"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by avgazn on 2010-06-22
I installed Ubuntu 10.04 and I downloaded some drivers and updates my nVidia driver. I went to restart my computer and instad of restarting it, I just shut it off. I turn it on again and when grub loads up and selects the first choice it doesn't load up to the main screen. Instead it asks for my name and password. After that it seems like just a normaml terminal. How can I boot up my desktop?

---

### Post by alphacrucis2 on 2010-06-22
> **avgazn said:**
> I installed Ubuntu 10.04 and I downloaded some drivers and updates my nVidia driver. I went to restart my computer and instad of restarting it, I just shut it off. I turn it on again and when grub loads up and selects the first choice it doesn't load up to the main screen. Instead it asks for my name and password. After that it seems like just a normaml terminal. How can I boot up my desktop?

What happens if you type

```
startx
```

after logging in?

---

### Post by tejashs on 2010-06-22
I am facing the same problem. STARTX command works fine but it goes directly to ubuntu. I cant choose whether to go into ubuntu or kubuntu.

But once in about 5 to 10 times i boot it starts normally without having to use STARTX command.

---

### Post by Perfect Storm on 2010-06-22
> **avgazn said:**
> I installed Ubuntu 10.04 and I downloaded some drivers and updates my nVidia driver. I went to restart my computer and instad of restarting it, I just shut it off. I turn it on again and when grub loads up and selects the first choice it doesn't load up to the main screen. Instead it asks for my name and password. After that it seems like just a normaml terminal. How can I boot up my desktop?

When you say you downloaded the drivers - was it through the "Hardware Drivers" option, or did you install the driver manually?
Do you have any unofficial sourcelist in your repositories?

---

