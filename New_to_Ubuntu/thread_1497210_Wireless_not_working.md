---
title: "Wireless not working"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by camn on 2010-05-30
It's not showing any wireless connections... What can I do to fix it?

---

### Post by nhasian on 2010-05-30
temporarily connect your computer to the internet via the ethernet port until we can get your wireless adaptor to work.  in a terminal type:

```
sudo apt-get update && apt-get upgrade
```

then check to see if there are any hardware drivers you can enable for your wifi adaptor.  please also make sure that the physical hardware switch is ON for your wifi adaptor.  sometimes its a switch on the outside of your laptop and sometimes its a keyboard combination to enable/disable it.  also give us the output of this terminal command:

```
lshw -C network
```

---

### Post by camn on 2010-05-30
> **nhasian said:**
> temporarily connect your computer to the internet via the ethernet port until we can get your wireless adaptor to work.  in a terminal type:

```
sudo apt-get update && apt-get upgrade
```then check to see if there are any hardware drivers you can enable for your wifi adaptor.  please also make sure that the physical hardware switch is ON for your wifi adaptor.  sometimes its a switch on the outside of your laptop and sometimes its a keyboard combination to enable/disable it.  also give us the output of this terminal command:

```
lshw -C network
```
Never mind, fixed it >_<
Just hardwired it and went to the hardware drivers thing and installed it...

---

