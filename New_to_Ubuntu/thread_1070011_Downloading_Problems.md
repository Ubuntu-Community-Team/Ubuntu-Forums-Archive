---
title: "Downloading Problems"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by andrija03 on 2009-02-14
Hello everyone,
I am having problems with downloading or even updating Ubuntu 8.10. Every time I try to download anything, I get the following message 

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Can anybody please tell me how I can fix this problem!

---

### Post by hyper_ch on 2009-02-14
do you have any software maanger open? e.g. synaptic, add/remove, adept?

---

### Post by llamabr on 2009-02-14
It sounds like you're trying to dload two things at once, but in two different places.  If you're running apt-get in one window, and then try to do it in another, you'll get that lock error.

Luckily, you can dload many things at once using apt-get, or whatever other app you're using.

---

### Post by yeats on 2009-02-14
This is the message you will get if you try to run an update when another program is already using the apt-get process.  If you have "Add/Remove Programs" open at the same time as the Synaptic, or are running

```
sudo apt-get update
```

in the terminal while one of those other programs is open, this is the message you will get.  Make sure only one update/install program is open at a time and try again.

---

