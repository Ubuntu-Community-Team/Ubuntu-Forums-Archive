---
title: "Removing a directory in shell starting with &quot;-&quot;"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by firefly2005 on 2009-11-01
Hi guys, just a simple question which has got me rather puzzled.

i have a series of folders starting with - and then a number, for example -340. How can i remove all of them in shell?

cheers in advance :p

---

### Post by mobilediesel on 2009-11-01
> **firefly2005 said:**
> Hi guys, just a simple question which has got me rather puzzled.

i have a series of folders starting with - and then a number, for example -340. How can i remove all of them in shell?

cheers in advance :p

I tried it and can't create or delete directories with "-" at the beginning. It's possible from a gui like Nautilus or Thunar, though.

---

### Post by Nimless on 2009-11-01
> **firefly2005 said:**
> Hi guys, just a simple question which has got me rather puzzled.

i have a series of folders starting with - and then a number, for example -340. How can i remove all of them in shell?

cheers in advance :p

from rm man page : 

To  remove a file whose name starts with a `-', for example `-foo', use
       one of these commands:

              rm -- -foo

              rm ./-foo

---

### Post by mobilediesel on 2009-11-01
> **Nimless said:**
> from rm man page : 

To  remove a file whose name starts with a `-', for example `-foo', use
       one of these commands:

              rm -- -foo

              rm ./-foo

rm for files and rmdir for directories, that works with both! You helped after I only *kinda* helped.

That just shows there's always more to learn and at least half of it will come from the man pages..

---

### Post by firefly2005 on 2009-11-01
cheers everyone. :p problem solved

---

