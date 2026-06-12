---
title: "After 10.04 update, Avant Window Navigator not starting at start up..."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-04-30
I had AWN starting fine with 9.10 but since the update I have to manually start AWN now from accessories. It's not a huge problem, but just somewhat of a annoyance.  Has anyone experienced this and YES, I do have start at startup checked under AWN settings.  Any ideas?

---

### Post by madjr on 2010-04-30
install latest version

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by mcoleman44 on 2010-04-30
Is it listed under startup Applications?

---

### Post by joenewtzie on 2010-04-30
> **mcoleman44 said:**
> Is it listed under startup Applications?

It is listed under startup Applications under ubuntu but I just installed Ubuntu tweaks and added the command to start it up through that, i'll restart it and see what happens though.

---

### Post by nmcgrew on 2010-04-30
I have done all of the above and it still will not start up automatically since the upgrade to 10.04.  I have to manually go to Applications to start it.  I have been searching all morning for a fix and cannot find one.

---

### Post by mcoleman44 on 2010-04-30
In startup applications it says:
```
avant-window-navigator --startup
```
Change it to:
```
avant-window-navigator
```
See if that takes care of it.

---

### Post by nmcgrew on 2010-04-30
It did!  Thank you so much.  It was a little thing but annoying and now it's fixed.

---

### Post by mcoleman44 on 2010-04-30
Glad I could help! :)

---

### Post by RazorV on 2010-08-04
Great Fix!   Thanks so much!  It worked like a charm!  

Cheers from Sarasota, FL

Greg

---

