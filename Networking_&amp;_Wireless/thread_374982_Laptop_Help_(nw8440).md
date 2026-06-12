---
title: "Laptop Help (nw8440)"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Voltaic Shock on 2007-03-03
I have an nw8440 from work that I installed Ubuntu on (dual boot).  I can plug in a cable and it gets an IP address but I can't visit any websites or update Ubuntu.

Are there any commands you need me to run to help me out.

Voltaic Shock

---

### Post by chili555 on 2007-03-03
It sounds like you have a DNS problem. Please do the following commands:
ping -c3 [www.google.com](www.google.com)
ping -c3 64.233.161.104

If you get packets returned from 64.x but none from google, then you are lacking proper DNS nameservers in /etc/resolv.conf. Sometimes, you can try to repopulate /etc/resolv.conf by doing sudo ifdown eth0 followed by sudo ifup eth0. Then try the above pings again. If you have the same result, then the command route -n will tell you your gateway IP address, usually something like 192.168.x.x.

sudo gedit /etc/resolv.conf and add:```
nameserver 192.168.x.x
``` or whatever your gateway IP is.

Try the pings above and you should be good.

---

### Post by Voltaic Shock on 2007-03-03
Well at one point it I couldn't ping them then now it says no network found.

I am now running the sudo ifdown eth0 and then the sudo ifup eth0.  I am hoping that works.  I have also put in my IP from what my router says.

route -n give just gives me blank info.

Is there anything else I can try?

Voltaic Shock

---

### Post by Voltaic Shock on 2007-03-03
Well I got it to Ping [www.google.com](www.google.com) and it says 3 sent and all are lost.

Is there anything else that I should try?

Voltaic Shock

---

