---
title: "[SOLVED] Screen shifted?"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Slacker20 on 2008-12-24
I am new to Ubuntu and just installed Ubuntu 8.04 on my desktop after installing YDL6.1 on my PS3.

I know this is probably a very simple fix, but I am not familiar with Linux or its commands yet.  My screen is shifted to the left about 1/4", and I haven't figured out why or how to fix it.  I know that on some monitors there are buttons to adjust this, but on my ViewSonic monitor there isn't.

Thanks in advance,
~Slacker20

---

### Post by oilchangeguy on 2008-12-24
> **Slacker20 said:**
> I am new to Ubuntu and just installed Ubuntu 8.04 on my desktop after installing YDL6.1 on my PS3.

I know this is probably a very simple fix, but I am not familiar with Linux or its commands yet.  My screen is shifted to the left about 1/4", and I haven't figured out why or how to fix it.  I know that on some monitors there are buttons to adjust this, but on my ViewSonic monitor there isn't.

Thanks in advance,
~Slacker20

true some monitors have an auto button. but yours still should have a menu button. this is not something you can fix with a command. it's not an operating system issue. it's a monitor issue.

---

### Post by nhasian on 2008-12-24
are there any restricted video drivers you need to install?  under System -> Administration -> Hardware Drivers.

if not, type this in a terminal and reply with the output:

```
lshw -C display
```

---

### Post by oilchangeguy on 2008-12-24
> **nhasian said:**
> are there any restricted video drivers you need to install?  under System -> Administration -> Hardware Drivers.

if not, type this in a terminal and reply with the output:

```
lshw -C display
```

this is a waste of time. all the op needs to do is locate the menu button on the monitor. and then locate the side to side menu, and shift it over. 30 seconds and it's done.

---

### Post by nhasian on 2008-12-24
I was just taking him for his word when he said his monitor had no buttons.  changing the resolution and/or frequency on a CRT monitor may recenter the display as well.

> **oilchangeguy said:**
> this is a waste of time. all the op needs to do is locate the menu button on the monitor. 

---

### Post by oilchangeguy on 2008-12-24
> **nhasian said:**
> I was just taking him for his word when he said his monitor had no buttons.  changing the resolution and/or frequency on a CRT monitor may recenter the display as well.

the op needs to look a little harder. have you ever seen a monitor with no way to adjust the picture?

---

### Post by Slacker20 on 2008-12-24
Wow... *bangs head into a brick wall* There's 4 tiny buttons on the back/side of the monitor that I had to get a flashlight to find, then took about 5 minutes just to reach them and figure out which button did what.

Thanks anyways though ](*,)

---

