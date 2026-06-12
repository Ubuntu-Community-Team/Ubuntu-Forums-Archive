---
title: "Starting Up Error"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Nosss on 2008-12-11
hi, I have an Asus X70S Series with an ATI Radeon 2400 HD card. I have installed Ubuntu however I have never seen the desktop. It is Ubuntu 8.10 and I have searched everywhere for a solution that works and none obviously dont. Basically it says " Screens found, but none hav a usable configuration" What happens is once loading Ubuntu, it shows loading bar then a black screen then throws me into a terminal and I have tried like the sudo dpkg-reconfigure xserver-xorg but I get stuck at a screen cos it says "over writing possible-customised configure file" so I have tried lots. Any ideas..how do I configure it? 

Nos

P.s I downloaded Qemu and emulated Ubuntu through that and it came up with the desktop as it should.

---

### Post by DaGrimReefah on 2008-12-19
Try

```
sudo aticonfig -initial
```

---

### Post by scorchgeek on 2008-12-19
Boot into recovery mode (it's an option on the boot menu) and select "Fix X Config".

---

### Post by Nosss on 2008-12-26
> **DaGrimReefah said:**
> Try

```
sudo aticonfig -initial
```

It came up with 

Sudo:aticonfig:command not found

any other ideas?

---

