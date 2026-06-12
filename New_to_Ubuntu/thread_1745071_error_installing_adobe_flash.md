---
title: "error installing adobe flash"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by antiblizzard on 2011-04-30
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

This is the error message I get when trying to install adobe flash player any help with be thankful.

---

### Post by TeoBigusGeekus on 2011-04-30
Could you be a bit more specific?
How did you try to install it?
What was the (exact) error message it gave you?

---

### Post by antiblizzard on 2011-04-30
I installed it or tried through the software center and that was the exact message it gave me

---

### Post by TeoBigusGeekus on 2011-04-30
Open a terminal, give this
```
sudo apt-get install flashplugin-nonfree
```
and post us any error messages.

---

### Post by antiblizzard on 2011-04-30
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I am getting this error now

---

### Post by TeoBigusGeekus on 2011-04-30
Close the software centre and repeat the procedure.

---

### Post by antiblizzard on 2011-04-30
Still telling me the same error plus this

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)

---

### Post by TeoBigusGeekus on 2011-05-01
Do you have synaptic open as well?

---

