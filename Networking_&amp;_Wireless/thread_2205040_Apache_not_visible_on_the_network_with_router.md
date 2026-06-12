---
title: "Apache not visible on the network with router"
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by nakren on 2014-02-11
Hello. I have router tp-link - i oppened port 80 for the server - 192.168.0.2 
In PC answer to $ sudo ufw numbered is :
80               ALLOW         192.168.0.0/24
80               ALLOW         Anywhere (v6)
and i wrote :
sudo iptables -A INPUT -p -tcp --dport 70 -j ACCEPT  ..... 
but i my apache is still not avalaible in network.... only in the local pc's...... :confused::confused::confused::confused::confused:
PLEASE HELPPPPPPPPPPPPPPPPPPPP!!!!!

---

### Post by nakren on 2014-02-11
And i think the problem is not in the router because i connect to SERVER WITH SSH please HELP!!!

---

### Post by Lars Noodén on 2014-02-12
You maybe meant --dport 80 rather than 70 for HTTP.  Also 443 is needed for HTTPS.  If it's still blocked, then post your other iptables rules because -A appends the rule and there might be some earlier rule blocking it.

---

### Post by nakren on 2014-02-12
In the message i mistake i opened port 80 in iptables!!

---

### Post by Lars Noodén on 2014-02-12
Do you have a second machine on the same LAN which you can use to test availability?  If it works with the second machine on the same LAN then the problem may lie with the configuration of your modem/router.  But remember that the external IP address of your modem/router might not be available from within the LAN, not all devices can handle that.

---

### Post by nakren on 2014-02-12
No i dont have second machine. But and i think the problem is in rooter.... my router is tp-link.. how can i fixed? do you have any ideas?

---

### Post by Lars Noodén on 2014-02-12
Most diagnosis is easier with a second machine.  The configuration of the router varies from model to model and brand to brand, so that's something you'll have to work out for yours.  

You can try checking if you can see your ports 80 and 443 externally [http://canyouseeme.org/](http://canyouseeme.org/), but that's of limited value.  It will say if they are open which might imply that they are also forwarded.  

Are you sure that your router allows access to the external IP from the LAN?  Some don't.  It might be that your machine is visible from the outside already.

---

### Post by nakren on 2014-02-12
Error: I Could not see you service on 37.143.251.119 on port (80) or (443)  Reason : Connection refused.
WHY? I open the port from iptables, ufw, and in my router 
[http://www.flickr.com/photos/117303164@N07/12479274053/lightbox/](http://www.flickr.com/photos/117303164@N07/12479274053/lightbox/)

---

### Post by Lars Noodén on 2014-02-12
It is also possible that the ISP blocks those ports.  But first I would check from a second machine on the same LAN to be sure that everything is set up correctly on your end.  That it works from the same machine is a good sign, but it's necessary to check from outside that machine, too.  Do you know anyone that can bring over a notebook or laptop and plug it in?

---

### Post by nakren on 2014-02-12
It dont work from another machine..... And i call in the ISP and they dont block , but they told me my port is not opened ...... why ?

---

### Post by Lars Noodén on 2014-02-12
Ok.  That narrows it down. What about trying ufw again?

```

sudo ufw reset
sudo ufw enable
sudo ufw allow http
sudo ufw allow https
sudo ufw status numbered

```

It may have been that -A (appending) a rule put it in the wrong location and you should let ufw figure things out.

---

### Post by nakren on 2014-02-12
Offff still the same. I think my router port forwarding dont work.

---

### Post by Lars Noodén on 2014-02-12
One more thing to check.  Is the ip you are forwarding to in your router the same as the one your machine *currently* is using?  With DHCP the ip can change a little unpredictably.

---

