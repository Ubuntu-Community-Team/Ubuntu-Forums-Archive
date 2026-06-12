---
title: "dpkg was interrupted Update ERROR Message"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by lukelogandennis on 2009-03-17
First off let me start by saying hello, and that I do not have much experience with Unbuntu. I'm running 8.04 on my laptop dual boot with Windows Vista. (Eww, gross I know.) 

For a while now, it has needed to update some stuff, but I keep getting an error after trying.

An error occured
The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a'to correct the problem.
E: _cache->open() failed, please report.

Now, what does this mean, and what do I do to fix it?
Thanks for any help you can give.:D

---

### Post by taurus on 2009-03-17
Close down the update manager.  Then, type these commands into a terminal, one at a time.

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rattking on 2009-03-17
Hi
open a Terminal and tpye
sudo dpkg --configure -a

that will continue configuring the packages that got interrupted
reload the package manager and update again
if may also ask you to run
sudo apt-get -f install

---

### Post by lukelogandennis on 2009-03-17
*Alright, so I tried typing that into the terminal. But when it asks for the password like normal. It will not let me type anything. All I can do is hit enter.*

Alright, I got to work. Thanks for your help!

---

### Post by taurus on 2009-03-17
When you type in your password, it doesn't show on the screen, not even *****.  In fact, the cursor doesn't even move.  That's the way it is so just make sure you type the same password that you log in with and hit Return.

---

