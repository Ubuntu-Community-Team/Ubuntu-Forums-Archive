---
title: "How to Run a fix"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by wmunsch on 2010-03-03
I installed compix for the cube and know when I try to download my updates it gives me an error E:dpkg and says to run 'Sudo pdkg-configure-a'  I'm knew to ubuntu so how do you run this correction.  Where do you go to run it

---

### Post by tacantara on 2010-03-03
Run the command, without the quotes, in the Terminal (Applications > Accessories > Terminal).  The command starts with sudo, which allows you temporary root privileges to execute the command.  As such, you will be prompted for your password.  When you type your password, it will not appear on the screen.

---

### Post by philinux on 2010-03-03
> **wmunsch said:**
> I installed compix for the cube and know when I try to download my updates it gives me an error E:dpkg and says to run 'Sudo pdkg-configure-a'  I'm knew to ubuntu so how do you run this correction.  Where do you go to run it

Run it in a terminal. Copy and paste from below.

```
sudo dpkg --configure -a
```

---

### Post by tacantara on 2010-03-03
> **philinux said:**
> Run it in a terminal. Copy and paste from below.

```
sudo dpkg --configure -a
```


Good catch on the syntax of the command, philinux.  That one slipped right by me.

---

