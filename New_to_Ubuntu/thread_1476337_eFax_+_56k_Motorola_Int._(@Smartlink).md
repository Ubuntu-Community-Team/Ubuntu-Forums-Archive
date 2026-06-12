---
title: "eFax + 56k Motorola Int. (@Smartlink)"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by LOIREE on 2010-05-07
Hi all!

Installed eFax, trying to receive fax using Motorola modem. It is internal modem, class 1. Slmodem daemon and ungrab-winmodem complied and running. When receiving fax from faxmachine, it comes up empty. I traced the problem to the following:

```

efax-0.9a Warning: timeout after command
efax-0.9a Error: timeout after command: +FTH=3

```No other errors that I've noticed. I could post full log, but I guess it will not help much. Yes, received data is 0 and I've tried -ozzz and -ozzzz (naturally separately), in case there was just not enough delay. I also tried using -w switch, as I'm using S0=2 (reply after 2 calls). Nothing seems to help. Any ideas? Anyone?

---

### Post by madjr on 2010-05-07
efax has a linux version ?

---

### Post by LOIREE on 2010-05-08
> **madjr said:**
> efax has a linux version ?
Its efax-0.9a @ Ubuntu 10.04.

---

### Post by LOIREE on 2010-05-08
Also, to note, I followed this guide exactly (except used latest version of slamr and ungrab winmodem): [http://ubuntuforums.org/showthread.php?p=5357553](http://ubuntuforums.org/showthread.php?p=5357553)

---

### Post by LOIREE on 2010-05-08
Please? Anyone? :roll:

---

### Post by madjr on 2010-05-08
hmm if efax has a linux version then why cant they give you some support after you already purchased the product from them?

---

### Post by LOIREE on 2010-05-10
> **madjr said:**
> hmm if efax has a linux version then why cant they give you some support after you already purchased the product from them?

Hello?! [http://www.cce.com/efax/](http://www.cce.com/efax/) NOT EFAX.COM!!! What's wrong with you?

---

### Post by LOIREE on 2010-05-11
Bump!

---

