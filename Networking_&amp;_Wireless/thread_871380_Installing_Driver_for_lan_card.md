---
title: "Installing Driver for lan card"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by sameergoel66 on 2008-07-26
Hi i am a linux newbi, the Lan card comes with driver for linux in tar.gz form. How do i install it.

---

### Post by ibutho on 2008-07-26
What type of LAN card is it? Does it not work out of the box with Linux? Can you let us know what chipset the card uses by running
```
sudo lshw -C network
```
If the driver it a tarball, you need to extract the contents and look at the README or INSTALL file for details on how to install it.

---

### Post by JagDragon on 2008-07-26
Extract it using ```
tar -xjf tarball.tar
```

---

