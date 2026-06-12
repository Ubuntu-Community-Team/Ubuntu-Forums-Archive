---
title: "oh no."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by ericgds on 2009-01-22
When I go to the synaptec package manager it says:  E: dpkg was interupted, you must manually run 'dpkg --configure-a' to correct this problem.
E:_ cache -> open()failed, please report.

Any advice on how to manually run that.  I typed in what was in quotes in the terminal and it didn't work.

---

### Post by taurus on 2009-01-22
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ericgds on 2009-01-22
> **taurus said:**
> Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure-a
sudo apt-get update
sudo apt-get upgrade
```

when I type the first line it says --configure-a is not an option.

---

### Post by taurus on 2009-01-22
There is a space between --configure and -a.  Try that again.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kansasnoob on 2009-01-22
Copy and paste.

---

### Post by ericgds on 2009-01-22
> **taurus said:**
> There is a space between --configure and -a.  Try that again.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

OK that worked, thanks.  Now it says I have 3 broken packages and need to use the broken filter to fix them.  I can't find the broken filter.

---

### Post by travmon69 on 2009-01-22
close package manager and use terminal  do sudo apt-get -f install

---

### Post by ericgds on 2009-01-22
> **ericgds said:**
> OK that worked, thanks.  Now it says I have 3 broken packages and need to use the broken filter to fix them.  I can't find the broken filter.


Hey, I think I just found it.

---

### Post by ericgds on 2009-01-22
> **travmon69 said:**
> close package manager and use terminal  do sudo apt-get -f install

I just saw this reply.  I think I somehow fixed it while I was playing around in synaptec.  should I do what you suggested anyway?

---

### Post by travmon69 on 2009-01-22
i came across a few problems with synaptic it is best i think to use apt-get through terminal.  that command will try to fix broken packages. you should search for how to fix broken synaptic and  save all the commands some where to have quick access to be able to copy an paste them into a terminal.

---

