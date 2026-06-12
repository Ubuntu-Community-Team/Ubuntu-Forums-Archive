---
title: "Sysrq recognized as &quot;Print&quot;"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by kesre on 2009-01-20
Ok, I know that Sysrq keys are important for safely rebooting in crashes
(which, surprisingly, I've been getting for a while... but thats a whole different thread...)

Anyhow, I have a Compaq Presario V6000 notebook, with 88 keys

Sysrq (as labeled on the keyboard) is accessed by holding down the FN key and pushing delete.

However, when I was looking at mappings to troubleshoot this problem, the input was recognized as prtscrn, (as was the real prtscrn key)

how can I remap sysrq or get Ubuntu to recognize the keyboard layout?

---

### Post by adult swim on 2009-01-20
have you tried ctrl+alt+print

---

### Post by kesre on 2009-01-21
yes

I've tried alt+fn prtscrn, alt+fn sysrq, alt [sysrq] alt [prtscrn] ctrl+alt+prtscrn, ctrl+fn....
and so on  

I base the 'successful or not' on if my computer reboots when I hit the combination plus "b" (after the REISU.. thing)

---

### Post by adult swim on 2009-01-21
hmmm maybe try hitting ctrl+alt+f1 and then mess around with those combinations.  if one happens to work, there will be output on the screen.  to get back to gui hit ctrl+alt+f7

---

### Post by kesre on 2009-01-21
thats just a shell environment, no?

during a kernel panic or other freeze, those commands won't work

---

### Post by adult swim on 2009-01-21
it is a shell and while it may not work in a kernel panic, testing on a stable environment may make it easier for you to find the correct combination of keys for sysrq.

---

### Post by JBarnes on 2009-05-13
I've also had this problem on a Compaq presario C700, running Intrepid. Any ideas anyone?

---

