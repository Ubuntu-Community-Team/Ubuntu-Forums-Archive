---
title: "VMWare issue"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by t1nm@n on 2010-06-27
hello i wanted to try linux and windows from vmware.
so i installed both windows and backtrack( idonloaded vmimage)
after installing vmtools in both ...i'm able to get internet in windows but not in bt3.
help me setup anetwork so that i can practise tutorials on ssldump and other tools...

please help me

P.S i use vmware player

---

### Post by yeleek on 2010-06-28
Have you even started the networking in BT3?

At a terminal prompt - does ifconfig give you a valid ip address, can you ping your default gateway?

Lots of BT3 in vmware stuff online...  and to be honest, if you are learning, start with bt4.

---

### Post by CharlesA on 2010-06-28
My guess is that networking isn't started on BT3. Personally I'd start learning how to use BT4, since it's the newer release. :)

---

### Post by varunendra on 2010-06-28
Try this command```
/etc/init.d/networking start
```If everything else is on default settings, and you have a DHCP server on your network, it should start the networking.

PS: I tried it successfully on BT4. Can't say about BT3.

---

### Post by laithbsoul on 2010-06-28
If your using vmplayer you'd be better off using virtual box as its open source and free and try BT4

---

