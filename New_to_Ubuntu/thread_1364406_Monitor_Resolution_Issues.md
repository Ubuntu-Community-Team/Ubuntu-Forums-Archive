---
title: "Monitor Resolution Issues"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by petgraveyard on 2009-12-25
I know this has probably already been posted somewhere, and I've actually been trying to follow the directions in the Wiki, but to no avail.

I just installed 9.10 on a fairly old workstation (2002 Dell), and I'm having trouble getting the monitor working.  Ubuntu is telling me that the max resolution is 800x600 (wrong) and that my only refresh rate is 60Hz (obviously wrong, since there's a nice line going straight down the screen as I speak).  I try to run sudo dpkg-reconfigure xserver-xorg and NOTHING HAPPENS.  I'm not kidding.  No error, no nothing, it stalls for a second or two and then gives me a prompt again.

Can anyone help me out here?

Thanks!

---

### Post by pi.boy.travis on 2009-12-25
Can you give us any information about the video card?

---

### Post by petgraveyard on 2009-12-25
> **pi.boy.travis said:**
> Can you give us any information about the video card?

Hmm...it's onboard Intel graphics, if that helps.  Is there a command I can use to get you any more specific information?

---

### Post by Sum Requiem on 2009-12-25
lspci | grep VGA

can give more info

---

### Post by petgraveyard on 2009-12-26
> **Sum Requiem said:**
> lspci | grep VGA

can give more info

Output:

```
.00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```

Any ideas?

---

### Post by sharaq on 2009-12-26
**go to this link, this will help you ....**

        [http://ubuntuforums.org/showthread.php?p=8560183#post8560183](http://ubuntuforums.org/showthread.php?p=8560183#post8560183)

---

