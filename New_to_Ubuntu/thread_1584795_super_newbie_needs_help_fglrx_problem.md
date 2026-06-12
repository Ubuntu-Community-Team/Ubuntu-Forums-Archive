---
title: "super newbie needs help fglrx problem"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by morgan365 on 2010-09-29
just got ubuntu 10.04 64bit used as live cd everything worked but i dual installed and tried to boot but it said ubuntu in low graphics i checked run in low graphic for one session and the box went away but nothing happened and i couldn't do anything finally i unplugged the machine rebooted and the same message came up and gave me a troubleshooter that told me failed to load module fglrx(does not exist) (EE) no drivers available what can i do to solve this problem and thanks in advance

---

### Post by P4man on 2010-09-29
Did this happen upon the first boot after installing? Or did it happen after you tried installing the (so called "restricted") ATI drivers? What videocard do you have?

---

### Post by morgan365 on 2010-09-29
It happened after the install on the first boot.The video card is an onboard on my asus  m3a78pro  mother board

---

### Post by sandyd on 2010-09-29
> **morgan365 said:**
> just got ubuntu 10.04 64bit used as live cd everything worked but i dual installed and tried to boot but it said ubuntu in low graphics i checked run in low graphic for one session and the box went away but nothing happened and i couldn't do anything finally i unplugged the machine rebooted and the same message came up and gave me a troubleshooter that told me failed to load module fglrx(does not exist) (EE) no drivers available what can i do to solve this problem and thanks in advance
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad

```
Theirs a current issue with fglrx.

See instructions in signature.

---

### Post by P4man on 2010-09-29
Any problem with fglrx wouldnt happen upon first boot, as those drivers are not installed by default. Then again, he couldnt have gotten any error message about it either, so morgan365 are you *sure* you didnt click the popup asking to install the videocard drivers?

---

### Post by morgan365 on 2010-09-29
well i guess i can't be 100% sure and now i'm on my windows os but first thing in the morning i am going to try to boot ubuntu agian.When i turn on my pc it gives me a ubuntu option a ubuntu recover option 2 memory options and windows should i boot in ubuntu or ubuntu recovery also when i had the live cd in it did instruct me to get driver for 3d graphics and once i could get online i did download the driver i was instucted to

---

### Post by sandyd on 2010-09-29
> **morgan365 said:**
> well i guess i can't be 100% sure and now i'm on my windows os but first thing in the morning i am going to try to boot ubuntu agian.When i turn on my pc it gives me a ubuntu option a ubuntu recover option 2 memory options and windows should i boot in ubuntu or ubuntu recovery also when i had the live cd in it did instruct me to get driver for 3d graphics and once i could get online i did download the driver i was instucted to
just choose the ubuntu option.
ill give you a prompt to login.

login (your password don't be visible), and type the command I posted.
then type
```

sudo shutdown 0 -r
```

---

