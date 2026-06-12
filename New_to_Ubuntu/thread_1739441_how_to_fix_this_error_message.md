---
title: "how to fix this error message"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-04-25
note i just forgot how
note i tried to log out but still get
[sudo] password for ray: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by wolfen69 on 2011-04-26
```
sudo rm /var/lib/dpkg/lock
```
then
```
sudo dpkg --configure -a
```

---

### Post by rburkartjo on 2011-04-26
wolf that did not work i know what the problem i was trying to install sun java and couldnt figure how to accept the eula at the end. they have <ok> and i forgot(part of getting old) how to accept. what keys to press etc. spm would not let me fix the broken packages or would the command you have me work until i accept the eula and install java first. go figure

---

### Post by rburkartjo on 2011-04-26
wolf got it fixed i had to do this
you accept the license when asked by pressing tab then press enter


stupid me. tks for the above commands though you earlier posted those were the ones i used before

---

### Post by Miljet on 2011-04-26
You have to press the "tab" key to be able to accept the EULA.

---

### Post by Miljet on 2011-04-26
See you remembered it while I was typing. Good going.

---

