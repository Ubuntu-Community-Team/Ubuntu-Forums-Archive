---
title: "Very Odd Problem................."
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

Does anyone know how to fix this? I will try anything

---

### Post by Behel on 2005-05-20
Hello,

I can't say exactly what can be the problem... But can you give more information about your internet access?

Is it wireless? Cable? DSL? 
Is your connection through USB? Ethernet router? Are you using a PCMICA card?
Do you use a firewall? Have you checked that your network hardware is well installed?
Are you using a laptop?
Have you checked /etc/ppp/dsl-prvider  or /etc/ppp/provider if any?

You can maybe also try to modify /etc/ppp/options and change the time for MTU...

---

### Post by xbaez on 2005-05-27
I had the excact same problems, run pppconfig, edited some files at /etc/ppp
and the only solution was to run kppp as a non-privileged user (root), that is in the 'dialout' group

So now I use root, and I am able to connect to the internet

Hopefully that will be your case too

---

