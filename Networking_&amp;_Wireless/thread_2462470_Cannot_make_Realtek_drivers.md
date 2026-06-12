---
title: "Cannot make Realtek drivers"
date: 2021-05-21
forum: Networking &amp; Wireless
---

### Post by mp-raxxius on 2021-05-21
Last post on this topic was in 2009 and the helpful script linked there no longer exists. ^_^

Basically, I'm trying to install/make the Realtek ethernet card drivers but it seems to be getting caught on an infinite loop at the MAKE stage.

I've tried using just the ./autorun.sh script, but that hangs at the build/install stage.

Investigating further, I've tried running the various make stages by hand and have noted the following:
1) When Makefile is executed it seems to be trying to do all of its work in /lib/.../build, rather than the directory the files are actually located it.
2) Even if I create a /lib/.../build directory it then can't find a Makefile in there

If I copy all of the contents into /lib/.../build and then try and execute it then, it traps itself in an infinite loop. Instead of building it just:
1) Enters /src
2) Executes Makefile there
3) Enters /src from the root directory
4) Executes Makefile there
5) etcetera

Is there something basic I'm missing? I'm using sudo to execute autorun or do the make files by hand, so it shouldn't be a rights issue... (I would think)

---

### Post by Yellow Pasque on 2021-05-21
Most Realtek LAN drivers are already built into kernel. You probably don't need to 'make' them. What card/chipset do you have and what Ubuntu version are you running?
Start here:
```
lspci
```
or, if USB:
```
lsusb
```

---

### Post by praseodym on 2021-05-22
Do you mean this one from the past? Its now available directly
```

sudo apt install r8168-dkms
```

---

### Post by mp-raxxius on 2021-05-22
Thank you both for the responses. ^_^

I ended up just installing a new Intel ethernet card which was properly associated with the correct driver.

And thank you, praseodym... will give that a try if I need to get the first network adapter up and running again.

---

