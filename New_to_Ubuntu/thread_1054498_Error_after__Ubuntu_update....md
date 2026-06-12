---
title: "Error after  Ubuntu update..."
date: 2009-01-29
forum: New to Ubuntu
---

### Post by sdim on 2009-01-29
Hi,everyone.
I get the following error in Synaptic after a recent update.
Any ideas about what should be done?
Thank you.

---

### Post by kostkon on 2009-01-29
Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give
```
sudo dpkg --configure -a
```
it will ask for password, give yours.
and then 
```
sudo apt-get update && sudo apt-get upgrade
```
the above commands will fix the problem and apply any remaining updates.

After doing the above, you should be fine.

---

### Post by taurus on 2009-01-29
Make sure you shut down synaptic first before you run those commands from a terminal or it will complain about unable to lock.

---

### Post by sdim on 2009-01-30
```
sd@sd:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
sd@sd:~$ 

```

I did what you proposed (thank you for the answers),but I got the message above...(?)

---

### Post by taurus on 2009-01-30
Maybe try

```
sudo apt-get clean
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by sdim on 2009-01-30
It didn't work,but thanks anyway.

---

### Post by sdim on 2009-01-30
It's a bug...

---

