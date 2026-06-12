---
title: "How to share Internet?"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by MicroBoy on 2008-03-27
**How to share internet if the Server Computer is with Ubuntu 7.10(not server edition) and Client is Windows XP. The computers are connected with Switch.**

---

### Post by Athelstan101 on 2008-03-27
The following URL has some useful info for sharing the Internet connection, however, there were some bugs to do with connection sharing with certain Ubuntu versions:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by MicroBoy on 2008-03-27
THNX i will try it ok

---

### Post by ugm6hr on 2008-03-29
A basic GUI way to do it:
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Firestarter is in the repos (you will also need to install dhcp3-server).

---

### Post by MicroBoy on 2008-04-12
> **Athelstan101 said:**
> The following URL has some useful info for sharing the Internet connection, however, there were some bugs to do with connection sharing with certain Ubuntu versions:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)[B]In this tutorial when it says:
> 1. Start by configuring the network card that interfaces to the other computers on you network:
# ifconfig ethX ip Do I have to change "ip" with "192.168.0.1" ?[/B]

---

### Post by superprash2003 on 2008-04-12
yea

---

### Post by MicroBoy on 2008-04-13
> **superprash2003 said:**
> yea[B]If i let "ip" it doesn't work or the IP will find  automatically?

[/B]

---

### Post by superprash2003 on 2008-04-13
you have to replace ip with 192.168.0.1 or any other ip.. but dont leave it as "ip" ..you can also make it 193.169.0.1 .. your wish.. since you are new to this.. just follow that tutorial and use 192.168.0.1 as ip.. once you get it running.. you can do your bit of tweaking!!

---

