---
title: "Docky stopped working properly maybe something to do with composite"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by thorbs on 2010-10-14
After working well for some time, the mail app and weather app stopped working. It might have something to do with a message about docky needs composite to work properly. I am not sure what composite is though....

---

### Post by TeoBigusGeekus on 2010-10-14
Open terminal and type
```
gconf-editor
```
to bring up the configuration editor.
Go to Apps>Metacity>General>Compositing Manager and turn the value to true.

---

### Post by thorbs on 2010-10-14
got the editor up, found apps but there was nothing called metacity...

---

### Post by cariboo on 2010-10-14
If docky works well other than the weather and mail applets not working properly, you have another problem.

Have you tried removing and re-enabling the applets?

---

### Post by thorbs on 2010-10-14
Yes I tried that, but the applets does not remove complitely, settings and other things is still there when you turn it off/on. Maybe I need to completely reinstall docky. But I thought it was interesting to at least know what was happening as docky and applets was working perfectly the first couple of weeks.

---

### Post by zachthejones on 2010-10-14
I'm having the same issue - the problem is compositing, whether in compiz or metacity. I had desktop effects working perfectly and then after an update all of a sudden compositing wouldn't work. And when I try to start compiz, here's the error message I get:
```
compiz: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_property_to_quads

```

I had enabled the Compiz PPA, and read somewhere that might be the problem, so I disabled it, removed all the compiz packages and then reinstalled compiz - same problem.

Any ideas would be greatly appreciated...

---

### Post by GabrielYYZ on 2010-10-15
try system > preferences > appearance > visual effects > normal or extra.

if visual effects are set to none, docky stops working 'cause of compositing.

---

### Post by thorbs on 2010-10-30
Ok, I have identified the problem (I think). 

I have had the dockey on automatic startup when the computer starts. But the problem is something to do with the lock-in. The keyring comes after the dockey program in startup. In this way somehow it does not get activated when dockey starts up. 

On the other hand if I first start the computer and then manually startup Dockey the pop up with the keyring comes and after entering that dockey works fine.

I have tried to reverse the order of program start up, with out succes. Anybody have an idea of how to fix this, so Dockey can start up automatically on computer start, and the applets still work?

---

### Post by thorbs on 2010-11-01
Anyone?

---

### Post by CoolJohnB on 2010-11-05
You need to go to: sudo gedit usr/bin/docky and after the first line put sleep 5

I had the same problem and this solves it, everything works great.

---

### Post by thorbs on 2010-11-05
Sweet, thanks

---

### Post by usererror on 2011-02-26
> **CoolJohnB said:**
> You need to go to: sudo gedit usr/bin/docky and after the first line put sleep 5

I had the same problem and this solves it, everything works great.

That worked for me too, I just installed Docky for the first time.

---

### Post by webdesigncompanyla on 2012-10-17
none of this is working for me

i just installed ubuntu 12.04.1  

docky weather applet has never worked in the past either, would like to get it to work...

---

### Post by oldos2er on 2012-10-17
Old thread closed.

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

