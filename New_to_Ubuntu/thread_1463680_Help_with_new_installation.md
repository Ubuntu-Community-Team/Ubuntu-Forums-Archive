---
title: "Help with new installation"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by grobar87 on 2010-04-27
Hi,
i use karmic with separate home partition.My hard drive is /-18G /home-90G and swap space 2G.My question is how can i remove karmic and make a fresh install of lucid without losing data in my home partiton?I want to format only /root partiton,so is that posible?

---

### Post by ubunterooster on 2010-04-27
Yes it is, unless /home is encrypted. You want to do the "select partitions manually" in the install. Select your old home, to be the same as the new but _do not format it_

---

### Post by Axel-P on 2010-04-27
> **grobar87 said:**
> Hi,
i use karmic with separate home partition.My hard drive is /-18G /home-90G and swap space 2G.My question is how can i remove karmic and make a fresh install of lucid without losing data in my home partiton?I want to format only /root partiton,so is that posible?

Hey!

That's easy ;)

Just install lucid and tell him to install / in  your /dev/sda1 partition, just as you did before. Also tell him to mount /home in your /dev/sda2, just be sure not to ask the partition manager to format your /dev/sda2. Also, is no longer necessary (in most cases) to have a separate home partition. Lets say  you have only 2 partitions (swap and /) and you want to install a newer Ubuntu, well you would tell gparted to mount the new / in your old / but in the formatting process Ubuntu would recognize your old /home and keep it.

---

### Post by grobar87 on 2010-04-27
how to know is home partition encrypted?:confused:

---

### Post by ubunterooster on 2010-04-27
try to access it with the live CD. If it is encrypted:> **bodhi.zazen said:**
> 
The answer to your question depends on which tool you used to perform the encryption - LUKS or ecryptfs.
[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

It is most likely Ecryptfs

---

### Post by grobar87 on 2010-04-27
Thanks for help guys,i try live CD and it works.

---

