---
title: "problem after problem"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by linux_agony on 2009-04-19
Well I tried everything. I even moved to a new apartment with a new roadrunner hookup wired directly to my LAN card. I get online now but now my taskbar crashes. I try to restart it in the terminal but it won't respond to the keyboard. It's like every time you fix a problem there's a new one, it's like that game at carnivals where you hit the gopher. And as much as I like to stay up till 3 am playing that game, I've got bills to pay. I've got spreadsheets to work on and e-mails to answer. As much as I hate microsoft's talking dogs popping up, at least I can get my stuff done. It's been real yall.
Matt

---

### Post by acimmarusti on 2009-04-19
Try fully updating and then do this in the terminal:

```

sudo apt-get install linux-backports-modules-intrepid

```

These are more fixes that might help out in stopping the many crashes you are experiencing.

Also, since ubuntu is mostly a "bleeding edge" distro, this kind of stuff is bound to happen. If you want better stability then stick with the Long Term Support versions (Ubuntu Hardy Heron 8.04). If that still give you trouble, then I suggest you go with Ubuntu's parent distro, Debian which recently released its 5.0 version. It's extremely stable, but at the expense of using older better tested software.

---

