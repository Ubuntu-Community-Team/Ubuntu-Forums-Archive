---
title: "Battery life tips - Ubuntu 10.10"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by Manny Ribera on 2011-04-10
Hi everyone! I recently passed to Ubuntu from widows 7.
I'm still trying to decide what system to use.
So fa everything worked fine and everything is snappy!
BUT, the batterylife is horrible!!!
I use the same settings as with W7: Low screen luminosity, no wifi, no bluetooth etc. but the batterylife sis still very bad.
Do any of you have any durable solutions? Could you explain them to me?
I have a HP-pavillon dv5.

PS: I read that there's a way to reduce the recovery from idle(whatever that means) from ~400 to 80, how?

Thank you for your help.

---

### Post by kiddfroster on 2011-04-10
> **Manny Ribera said:**
> Hi everyone! I recently passed to Ubuntu from widows 7.
I'm still trying to decide what system to use.
So fa everything worked fine and everything is snappy!
BUT, the batterylife is horrible!!!
I use the same settings as with W7: Low screen luminosity, no wifi, no bluetooth etc. but the batterylife sis still very bad.
Do any of you have any durable solutions? Could you explain them to me?
I have a HP-pavillon dv5.

PS: I read that there's a way to reduce the recovery from idle(whatever that means) from ~400 to 80, how?

Thank you for your help.

You can install PowerTop, which is a utility that can tell you what is making your laptop use power. If you go into a terminal and run ```
sudo apt-get install powertop
```, it will install. Once it is done, run ```
sudo powertop
``` and follow the tips that it suggests.

Hope your battery life improves!!

---

### Post by ubudog on 2011-04-10
I would definitely recommend turning off any unnecessary Bluetooth devices, as these can eat up the battery.  Also, PowerTop is a good tool.  Good luck.

:-)

---

### Post by TuxNorris on 2011-04-10
Thanks, just tried this and it works :)

---

### Post by ubudog on 2011-04-10
Cool!

---

