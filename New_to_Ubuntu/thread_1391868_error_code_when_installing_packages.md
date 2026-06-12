---
title: "error code when installing packages"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by jacob_pikachu on 2010-01-27
Hey Everyone!

Whenever I try to install a package in terminal i get the following error code:

Errors were encountered while processing:
 eeepc-laptop-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)


The things that I install are still functional, I was just wondering about the error.
I have an eeepc 1008ha and am running UNR

Any help would be very appreciated

---

### Post by Hospadar on 2010-01-27
Probably at some point that package had some failure when updating or something.

A couple questions: is the installation a fresh-ish one (i.e. you didn't upgrade from 9.04 to 9.10)

You could try 'sudo apt-get install --reinstall eeepc-laptop-dkms' and see what happens

---

### Post by J V on 2010-01-27
I agree, you might have downloaded a melon package (apt-get downloads and starts dpkg which throws the error...)

---

