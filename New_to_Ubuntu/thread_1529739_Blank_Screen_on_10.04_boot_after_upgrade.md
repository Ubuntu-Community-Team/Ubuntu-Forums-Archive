---
title: "Blank Screen on 10.04 boot after upgrade"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by MelodicDaydreams on 2010-07-12
Disclaimer - Novice **Helping with a friends system

Just updated from 9.10 to 10.04.  Boot cycle now lands me on a blank screen.  I understand that means my video card is not jiving with the defaults of the OS.  In the GRUB menu I am trying to replace 'quiet' with an instruction that is more suited with what I'm guessing is an older intel video card.  
I am able to delete the 'quiet' line and add a line.  What is the trick to typing on the created line?
Thanks to anyone who can help!!!

Urgent response needed - PLEASE HELP :)

---

### Post by wojox on 2010-07-13
Try:

```
nomodeset
```

---

