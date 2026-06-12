---
title: "Spontaneous Shutdown"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by ElighCS on 2010-09-26
Hello Everyone I am relatively new to ubuntu but I am moderately computer literate. Twice today my AMD x86 Laptop system running ubuntu 10.04 has spontaneously hard switched itself, It sounded like it does when I hard switch the machine.
Thanks for your help.

---

### Post by sandyd on 2010-09-26
> **ElighCS said:**
> Hello Everyone I am relatively new to ubuntu but I am moderately computer literate. Twice today my AMD x86 Laptop system running ubuntu 10.04 has spontaneously hard switched itself, It sounded like it does when I hard switch the machine.
Thanks for your help.
have you checked if its overheating?

---

### Post by Mi11z on 2010-09-26
> **ElighCS said:**
> Hello Everyone I am relatively new to ubuntu but I am moderately computer literate. Twice today my AMD x86 Laptop system running ubuntu 10.04 has spontaneously hard switched itself, It sounded like it does when I hard switch the machine.
Thanks for your help.

Ahh someone beat me to it, yes it probably overheated, this is frequent with all computers and especially all laptops apart from mac's, it's because laptops are designed with "portability" in mind and not cooling and that brings me to another point cooling is the biggest problem with computing anyway, what i do to combat this is when i leave my pc on for a prolonged period of time for whatever reason (downloading) i leave the lid open and turn of the screen to save power, hope this helps. :)

---

### Post by bsalem on 2010-09-27
There are lots of things that can cause an OS or an app to crash. Look in /var/log for files that contain status messages for various parts of the system. /var/log/messages will often have messages about either a system crash or an aplication failure. Sometimes this info will be useful for getting debugging help. There is a GUI for the administrator to examine these logs,
if this is your personal system, you get admin privileges by giving your password when prompted.

---

