---
title: "Networking wont start after a reboot"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by wabbit46 on 2009-03-28
I am running ubuntu 8.04 LTS.

Every time I reboot my ubuntu machine it refuses to connect to the network.

Typing in a terminal session sudo /etc/init.d/ networking stop comes back with the message "RTNETLINK answers: No such process"

If I then enter sudo /etc/init.d networking start all is back to normal.

What do I need to do to make networking come up automatically on reboot ?

---

### Post by ronocdh on 2009-03-28
> **wabbit46 said:**
> I am running ubuntu 8.04 LTS.

Every time I reboot my ubuntu machine it refuses to connect to the network.

Typing in a terminal session sudo /etc/init.d/ networking stop comes back with the message "RTNETLINK answers: No such process"

If I then enter sudo /etc/init.d networking start all is back to normal.

What do I need to do to make networking come up automatically on reboot ?
I recommend you take a hard look at your /etc/network/interfaces file and see that that's configured correctly WRT your hardware.

Try starting a thread over in Wireless & Networking, and make sure to post your /etc/networking/interfaces in a codebox. Maybe someone there can help more!

---

