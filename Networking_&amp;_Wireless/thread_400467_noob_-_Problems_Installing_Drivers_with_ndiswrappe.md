---
title: "noob - Problems Installing Drivers with ndiswrapper"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by YarisPCA on 2007-04-03
I think  I've installed the drivers now, but I still have a problem. I got the message that the driver was installed and the hardware was present, but when I tried "depmod -a" I just got an error message stating

```
FATAL: could not open /lib/modules/2.6.17-10-generic/modules.dep.temp for writing: Permission denied
```

I'm not sure what is wrong. If it helps, this is a USB Microsoft MN-510 adapter. Thanks.

---

### Post by dbott67 on 2007-04-03
Did you precede the command with 'sudo'?

```
sudo depmod -a
```

---

### Post by YarisPCA on 2007-04-03
Woop! I guess I forgot. Thanks for replying so fast.

I tried sudo depmod -a and it asked for my password. I typed it in and hit enter but then noting happens. :confused:

---

### Post by YarisPCA on 2007-04-03
bump.

---

### Post by josephus on 2007-04-04
if depmod -a works properly it does not give any output.

not sure what you've done yet, so not sure how to help you from here.  from the limited description of the problem it sounds like you attached the windows driver to the ndiswrapper with success.  the next step then is to load up the ndiswrapper.
```
sudo modprobe ndiswrapper
```
if that works then type iwconfig,  you should see that a new wireless device installed.

---

