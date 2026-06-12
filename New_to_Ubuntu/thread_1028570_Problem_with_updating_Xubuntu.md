---
title: "Problem with updating Xubuntu"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by tomsax on 2009-01-02
I have installed Xubuntu on my laptop.  Update Manager tells me there are 101 updates available but when I try to load them or check them I get an error message:
____________

An error occured:

The following details are provided

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

______________


Needless to say I have no idea what this means or what I can do to remedy the situation.  Can anyone help me?

Tom

---

### Post by ibizatunes on 2009-01-02
Go to the terminal and copy and paste this commands in

```
sudo dpkg --configure -a
```
Will fix your issue

This can happen when the computer is turned off during a update

```
sudo apt-get update && sudo apt-get upgrade
```
This will install all updates available

---

### Post by tomsax on 2009-01-02
Thanks very much.  It indeed worked very well!

That was great!

---

### Post by pancakewagon on 2009-01-03
I was getting the same prob because it crashed during an up date... but I didn't know there was a command! So i just thought I had to reinstall. Thanks now i know i don't have to reinstall next time it happens! :D

---

### Post by efexD on 2009-01-03
This is how i did it.

```

sudo apt-get update

```

Oddly i had to restart the computer and the second time it worked.

---

