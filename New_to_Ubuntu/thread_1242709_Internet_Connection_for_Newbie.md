---
title: "Internet Connection for Newbie"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by arune1386 on 2009-08-17
This may be covered in "How tos" and if so, please bear with me.

I have a Dell Inspiron 1501, rather basic, with Windows XP as the OS. I have installed Ubuntu 8.10 from a CD and it seems to be working just fine.
My home network is connected to SHAW in Canada (BC) and uses a wireless Belkin Wireless G Router.  I have the "key" for that.
So, in a "put the pointy end of the bullet in first" way, how do I connect to the Internet?  I have tried and am totally confused with the various options and nothing seems to get me on line.
My intention is to roll over everything to Umbuntu as soon as I can get it on line.
Thank you for your assistance.

Willow

---

### Post by cariboo on 2009-08-17
How are connected to your router? Are you trying to connect via wired cable or via wireless? What have you tried so far? To check and see if your wireless device is detected, open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

The above command will create a file called network.txt that you can copy to your windows partition and the paste the output in your next post. The purpose of the command is to check and see if your hardware is detected properly, and that the driver is loaded.

BTW I'm using Shaw too, I have a mixed network of wired and wireless computers that all connect with zero problems.

---

