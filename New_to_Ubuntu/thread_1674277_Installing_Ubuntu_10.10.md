---
title: "Installing Ubuntu 10.10??"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by apanton06 on 2011-01-23
Basically I was looking to install Ubuntu 10.10 alongside Windows 7. Sorry if I go on a bit, but I want to make sure I install it correctly first time (had a few problems I first set up fedora).

1) I created a new primary partition in w7 (around 200GB). Do I need to create a swap partition beforehand as well, or can I do this during the install? Is this the right partition type?

2) I've read some posts on chainloading, in order to do so I would need to install GRUB on to the linux partition rather than the MBR. Is there an option to do this on the Ubuntu 10.10 install?

Also, if you have any useful step by step guides for the 10.10 install it would be appreciated.

Edit: I had 1 primary partition (windows 7 partition) and now I have the additional primary partition for Ubuntu.

---

### Post by Quackers on 2011-01-23
Before you go creating new primary partitions, you should check how many primary partitions are already in use on your hard drive. There is a maximum of 4 on any single disc (which would include an extended partition).
If you have a look in Windows in disk management screen it will tell you.

---

### Post by Paqman on 2011-01-23
Tbh, the easiest thing to do might be to just leave that space unformatted. That way you can just tell the installer to use the largest free space and it'll get on with it.

> **apanton06 said:**
> 
Also, if you have any useful step by step guides for the 10.10 install it would be appreciated.


The installer walks you through step-by-step, and you can run a web browser at the same time if you want to ask any questions.

---

