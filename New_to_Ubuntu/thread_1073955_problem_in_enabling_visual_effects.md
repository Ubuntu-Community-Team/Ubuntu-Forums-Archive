---
title: "problem in enabling visual effects"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by ellankavi on 2009-02-18
Hi I am using the 7.10 version of Ubuntu and I have problems in changing the desktop visual effects from 'none' to any other.. It says that  'Desktop Effects cannot be enabled' What can I do?

---

### Post by scorchgeek on 2009-02-18
You're probably missing the correct driver. Try going to Synaptic and searching for the name of your video card manufacturer to download the driver.

---

### Post by ellankavi on 2009-02-18
I have tried searching but i can't find what's wrong.. I am frustrated!](*,)

---

### Post by ellankavi on 2009-02-18
Just solved it .. it was

sudo apt-get install xserver-xgl

I saw that this had to be done explicitly for the Gusty :)

---

