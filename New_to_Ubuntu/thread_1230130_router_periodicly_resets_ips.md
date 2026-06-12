---
title: "router periodicly resets ips"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by deankovell on 2009-08-03
every couple days I have to have my roomate reset his router, or else I can't connect to the internet on my ubuntu system. I can boot into vista :( and connect just fine. also three other laptops in the house, all runnung xp, connect just fine. two previous roomates had the same problem on their macbooks. My roomate said the router , buffalo whr-g54s, resets the ip addresses every 48 hours. would someone help me correct my ubuntu system to properly deal with my given network situation. also, I'm use Wicd on Jaunty via ndiswrapper, with network admin uninstalled.

thank you.

---

### Post by hibliss on 2009-08-03
Tell him to set static IPs in the router based on MAC address.

---

### Post by deankovell on 2009-08-03
thanks hibliss
   He told me earlier I could get into the routers webpage and make some adjustments if I need to, but I'm still wanting to learn how to make my computer conform to the existing situation. I don't expect a command by command tutorial from anyone, but maybe some suggestions on what I should be consulting the almighty google about would be cool. 
Thanks.

---

### Post by hibliss on 2009-08-03
You can set a static IP on your end. That is what you want.

DHCP is where the router pushes whatever IP it wants to you.

Static IP is where you set it on the Computer end and the computer tells the router what IP it wants (and sets it even if it does not exist on the network). 

Get your current IP and google setting it up as staic so it won't change.

---

### Post by deankovell on 2009-08-03
thanks man

---

### Post by HavocXphere on 2009-08-03
Sometimes when the adsl pppoe connections here go fubar then the following works:
```
sudo dhclient eth0
```

That tries to grab a new addr from the router. The "eth0" part could be different on your PC (unlikely).

Or you could check the router config. Some routers can be remotely reset. (Try above first).

---

### Post by deankovell on 2009-08-03
Thanks havocXphere,
   Initially I didn't understand the issue well enough to explain what was happening correctly. I did figure out that it was the dhcp lease that was expiring. sudo dhclient wlan1 did renew the lease for 70 thousand and something seconds, and I think it'll terminate at some point in the next day after that.. Unless, I can't get it to connect again in a couple days, I'm gonna consider this solved. Thanks guys. 

I am also wanting to  look into why this isn't happening automaticly and how to make it happen automaticly. I will appreciate suggestions, but I think I know enough now to figure it out relatively quickly. I'll post the answers in case it helps someone else.

---

### Post by hibliss on 2009-08-03
The best solution is to set a static IP for the machine in the router's interface based on MAC address (not all routers have this option).

The next best solution is this -- [http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html")

Just set the address to your current settings that you are happy with.

---

