---
title: "actiontec gt701 &amp; dhcp"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by sneakers563 on 2007-02-07
Hi all,
I'm running edgy and I've got a problem with an Actiontec GT701 DSL modem.  Basically, if I cycle the power on the modem before turning on my computer, the computer gets a network address through dhcp and everything works if.  If, however, I don't cycle the power on the modem after shutting down the computer, the computer doesn't receive a net address when it boots up and I'm (obviously) unable to access the internet.  Essentially, I'm stuck shutting down the modem everytime I shut down the computer.

Any suggestions?  I tried using a static IP address but that didn't seem to fix the problem.

Thanks!

---

### Post by nrwilk on 2007-02-10
Here's a couple of threads which should help you out:
[http://ubuntuforums.org/showthread.php?t=192501&page=5](http://ubuntuforums.org/showthread.php?t=192501&page=5)
[http://www.ubuntuforums.org/showthread.php?t=134731](http://www.ubuntuforums.org/showthread.php?t=134731)

This is a common problem.  Your modem's DHCP server is trying to broadcast it's own IP as a DNS server, so your DNS entries are being overwritten.

In the last post of that second thread linked above is a way to make sure that the correct DNS entries are always in your resolv.conf file.

Hopefully this helps! :)

---

