---
title: "cannot connect ssh public ip"
date: 2015-01-31
forum: Networking &amp; Wireless
---

### Post by Hadaka on 2015-01-31
Hi, my ssh wont connect from outside the lan
I have 2 machines both setup as server/client and both work fine talking to 
eachother on 2 different networks,but refuse to connect using public/router ip.
the cursor just sits there,no error message...forever.
ssh -p22 [email]user@local_ip....works[/email]
ssh -p22 user@router/public_ip doesnt.
attached is a shot of my port-forward router
[ATTACH=CONFIG]259626[/ATTACH]
It's got to be something simple,but i am new to ssh and cant find it,
any suggestions?

---

### Post by jeremy31 on 2015-01-31
I never got it to work but hopefully your ISP is better.  This might help you with some troubleshooting [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by Hadaka on 2015-01-31
thanks,that was also something i did and it fails to connect.
I had this working a few months back, it seemed pretty straight forward
at the time.There are no fancy firewalls,no ufw,no fail to ban. It's just a
bare bones ssh utility.It has to be something simple ive overlooked, it works
fine in the local mode and i can ping the router. The port is not blocked "#" 
in /etc/ssh/sshd_config. I am without a clue.

---

### Post by efflandt on 2015-02-02
Are you trying to connect to your server from the internet, or from another computer on same LAN using your public IP? Many broadband routers do not do loopback (LAN2LAN via WAN IP) maybe to avoid IP spoofing. So you really should test it from something with an internet connection that is NOT on your LAN. Or you could ssh to a shell account somewhere on the internet (like sdf.org alias freeshell.org which is NetBSD) and then ssh from there back into your server.

That assumes that [www.canyouseeme.org](www.canyouseeme.org) shows the port open on your public IP.

---

### Post by papibe on 2015-02-02
Hi Hadaka.

The ability to connect to a machine from your local network using its public name, or IP, is called **NAT loopback** (read about it [here]("http://opensimulator.org/wiki/NAT_Loopback_Routers")). This an advance feature, and it is not supported by most consumer routers.

I would start by checking the router's documentation in the slim case it support it.

In case the router does not support this feature, you won't be able to access a machine in the LAN, from the LAN, using the router's public IP. In order to test remote access, you would have to do it from the outside. For instance, using your cell phone 3G/4G service, from a public library, or a friend's house.

I hope that helps. Let us know how it goes.
Regards.

---

### Post by Hadaka on 2015-02-03
Hi, yes i am aware that its not going to work with both machines on the same lan.
i have machine a and B, but i also have network A and B.  when i set up machines a and b
both server/client mode on network A or B (lan works fine) when i attempt to ssh to
computer a on network A from computer b on network B it fails. I had this working awhile back
so something has changed. I may just delete all and any refrence to ssh tomorrow and reload.
thanks for your input on this.

---

### Post by SeijiSensei on 2015-02-03
Try forwarding a random "high" port like 22222 back to the server's port 22. Then try connecting from outside using "ssh -p 22222 servername".  Any luck?

---

### Post by Hadaka on 2015-02-03
Thanks SeijiSensai , that reacted the same way, cursor just hangs, like it 
wants more data,,,and i have entered more and it still just sits there.
evenutally i get a time out message. I think rather than spend countless
hours on this, its just a home server for personal stuff, so no big deal. I
like being able to use places like coffee shops as an onramp, but i dont do
it very often. so, I am just going to delete any an all ssh files and reload.
I'l marked this solved once thats done and its working again. Thanks for
all input.

---

