---
title: "Can't view webpages"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by shendric on 2007-02-17
When I view my pages from the same machine that runs the server, I can see them no problem ([http://localhost/mypages)](http://localhost/mypages)), but when I try to view them from another machine on my network, I can't see them.  I get a "requested URL not found" error.  Is there something in my apache2 configuration that's wrong?

---

### Post by Floppyjoe on 2007-02-17
Youll have to change the localhost part to the Ip address of the server in the line:
[http://localhost/mypages](http://localhost/mypages)

to [http://IPOFSERVER/mypages](http://IPOFSERVER/mypages)

for example:
[http://192.168.1.100/mypages](http://192.168.1.100/mypages)

Otherwise the computer thinks you are looking for the URL on the computer you are using.

---

### Post by shendric on 2007-02-17
> **Floppyjoe said:**
> Youll have to change the localhost part to the Ip address of the server in the line:
[http://localhost/mypages](http://localhost/mypages)

to [http://IPOFSERVER/mypages](http://IPOFSERVER/mypages)

Yep.  Did that.  I've checked and rechecked the ip address, and it's the right one.

---

### Post by Floppyjoe on 2007-02-17
Is the port 80 open on the machine with the server? Maybe IPtables firewall blocking port 80?
I use firestarter to open the port on my server machine.

---

### Post by shendric on 2007-02-17
Could you explain how to use firestarter to open that port?  I'm not sure how to find out if that port is open.

---

### Post by shendric on 2007-02-17
Actually, just did a port scan, and I saw that 80 is open.

---

### Post by Floppyjoe on 2007-02-17
I installed the firestarter Gui from synaptic which is a front end for the IP tables firewall that I think is set up on Ubuntu by default.  You need to set up firestarter then click on the policy tab and then click on the allow service window then click on add rule then it will ask for Name of service and you choose HTTP and PORT you choose 80. Also the source is anyone if you want others to access the server or a specific IP address or range if you just want local access. Then click add to add the rule

---

### Post by Floppyjoe on 2007-02-17
Are you spelling the name of the requested URL right?

---

### Post by shendric on 2007-02-17
I'm not sure how firestarter could help here, as the firewall isn't even active.  I have not had problems with viewing pages before, just recently.  I don't know how recently, because I haven't had the need to try it before.

Could it be the router?  Although I've had this router before when accessing pages between machines.

---

### Post by shendric on 2007-02-17
Ok, another piece of information.  If I put in the server ip address on the local machine, rather than localhost, I get the same error.  This sounds more and more to me like a configuration issue, but I don't know.

---

### Post by Floppyjoe on 2007-02-17
Is your sever publishing to the internet? Are you forwarding port 80 to your server in router settings? Are you using a local lan IP or the IP that your ISP serves you?

---

### Post by shendric on 2007-02-17
Found it.  Somehow, my Apache's NameVirtualHost was listed as 127.0.0.1, so I only could view it through the loopback address.  I changed it to *:80, and it was all good.

Thanks, FloppyJoe

---

