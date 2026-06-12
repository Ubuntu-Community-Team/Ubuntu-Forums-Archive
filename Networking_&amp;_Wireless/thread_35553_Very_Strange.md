---
title: "Very Strange"
date: 2005-05-19
forum: Networking &amp; Wireless
---

### Post by veronica84 on 2005-05-19
Hello,

I am getting some odd bugs with Ubuntu 5.04. I love the distro and have converted from Windows and FC3. However after a week or so using Ubuntu I lose my PPPoE connection and cannot get it back online. I then have to reinstall. Have done this 3 times and just now after a reboot I have again lost PPPoE connectivity. 

This is the readout from the root terminal after I have done pppoeconf and set it up as per usual: 

root@Funky-Chicken:/home/veronica # plog
May 19 21:47:14 localhost pppd[8079]: Using interface ppp0
May 19 21:47:14 localhost pppd[8079]: Connect: ppp0 <--> eth0
May 19 21:47:14 localhost pppd[8079]: Couldn't increase MTU to 1500
May 19 21:47:14 localhost pppd[8079]: Couldn't increase MRU to 1500
May 19 21:47:17 localhost pppd[8079]: Couldn't increase MRU to 1500
May 19 21:47:17 localhost pppd[8079]: Remote message: Request Denied
May 19 21:47:17 localhost pppd[8079]: PAP authentication failed
May 19 21:47:17 localhost pppd[8079]: Couldn't increase MTU to 1500
May 19 21:47:17 localhost pppd[8079]: Couldn't increase MRU to 1500
May 19 21:47:17 localhost pppd[8079]: Connection terminated.
root@Funky-Chicken:/home/veronica #

Does anyone know how to fix this? I will try anything:)

---

### Post by kleeman on 2005-05-19
I am no expert on dsl but I seem to remember that mtu for pppoe should be set to 1492. The dslbroadband site has much info on this...

---

### Post by xbaez on 2005-05-27
I had the excact same problems, run pppconfig, edited some files at /etc/ppp
and the only solution was to run kppp as a non-privileged user (root), that is in the 'dialout' group

So now I use root, and I am able to connect to the internet

Hopefully that will be your case too

---

