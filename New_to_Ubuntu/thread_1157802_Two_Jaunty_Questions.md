---
title: "Two Jaunty Questions"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by myolbug on 2009-05-13
First, does Jaunty 64bit automatically come with 64bit Flash?

Second, is the FireFox NoScript extension really necessary?  Is there really a security risk in FF with Ubuntu?

Thx in advance!

---

### Post by ndefontenay on 2009-05-13
Hello,

Like for the 32bit version, no. You'll have to download it from the repository.

2) No idea. Can't help.

---

### Post by myolbug on 2009-05-13
> **ndefontenay said:**
> Hello,

Like for the 32bit version, no. You'll have to download it from the repository.

2) No idea. Can't help.

Re: 1).  I have an AMD 64bit system and I have Jaunty 64bit, so I am wondering if I have to re-download the 64 bit Flash like I did when I had 8.10

---

### Post by Keithhed on 2009-05-13
there is a sticky in the 64bit section of the forum that details the flash install ( 5 min process) 

I haven't encountered issues with ff running scripts, but I don't know the answer.  I mainly use Opera.

Hope this helps :)

---

### Post by Stunts on 2009-05-13
1) You just have to do ```
sudo apt-get install flashplugin-nonfree
``` to get flash on a 64 bit system.

2) "No script" can be useful to prevent _firefox specific_ vulnerabilities. I don't think there are any pages exploiting any Ubuntu vulnerabilities (if there are in fact, any).

Hope this helps.

---

