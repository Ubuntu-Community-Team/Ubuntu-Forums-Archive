---
title: "sharing connection"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by Rakeshvijayan on 2010-11-25
How to share IPv4 connection in ubuntu  am using two lancard i want give internet to other system .

---

### Post by JustinR on 2010-11-25
Sorry no one's responded so far! This was a pretty easy answer!

The way I'm going to show you requires an ethernet cord.

1. On the computer with internet, right click the network icon on the top panel and click 'Edit Connections', under the 'Wired' tab, click on your ethernet connection and press 'Edit'. Under the 'IPv4' tab, click the combination box called 'Method' and click the option 'Shared to Other Computers'.

Press 'Apply' and close out of it all, restart your computer.

After the computer is restarted plug in the ethernet cord to your computer and the other end into the computer that doesn't have internet.

Good luck! You should be sharing an internet connection now.

---

### Post by Rakeshvijayan on 2010-11-25
let me know is it possible via command prompt ....

---

### Post by JustinR on 2010-11-25
> **Rakeshvijayan said:**
> let me know is it possible via command prompt ....

If you want to look into it, this will probably be a good help:
[https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing)

---

### Post by viju on 2010-12-21
[QUOTE=JustinR;10160987]Sorry no one's responded so far! This was a pretty easy answer!

The way I'm going to show you requires an ethernet cord.

1. On the computer with internet, right click the network icon on the top panel and click 'Edit Connections', under the 'Wired' tab, click on your ethernet connection and press 'Edit'. Under the 'IPv4' tab, click the combination box called 'Method' and click the option 'Shared to Other Computers'.

Press 'Apply' and close out of it all, restart your computer.

After the computer is restarted plug in the ethernet cord to your computer and the other end into the computer that doesn't have internet.

Good luck! You should be sharing an internet connection now.[/UNQUOTE]

Above method worked Ubuntu 10.04 but did not work for Ubuntu 9.1.

My configuration is as follows.

PC1 Ubuntu 9.1,Ubuntu 10.04 and Winxp,2 network cards one connected to internet and other connected to PC2 by crossover cable.

PC2 Winxp and Mandriva2007

---

