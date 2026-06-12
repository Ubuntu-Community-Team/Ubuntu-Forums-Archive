---
title: "No SSH from external address"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by Joris_Bijvoets on 2015-02-08
I have an Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-45-generic x86_64)  installation which I want to use from an external IP address via SSH. The ip number is 192.168.0.58, SSH port is 22.

I have a Ziggo Ubee modem, which allows SSH forwarding with external IP 84.x.y.z. I have configured port forwarding at this modem for port 13358 to ip 192.168.0.58, port 22.

With my laptop I can reach the machine via SSH in two ways:
1. If my laptop is in the same network and use SSH to 192.168.0.58 port 22
2. If my laptop is in the same network and use SSH to 84.x.y.z port 13358

If I place my laptop in the network of my neighbour (with allowance and via Wifi), and try to connect to 84.x.y.z port 13358 I get a Connectoin Timeout. If I use another external network, I get the same error.

Some months before I used the same construction for another machine, which worked very well.

I can use SSH from my laptop to another external IP address.

I have already reset the cable modem, resetted it back to factory configuration, but it didn't help. I tried with the server configured as DMZ and 'not as DMZ'.

HELP! Where can I look further to solve this? Could it be some exotic ssh-parameter?

---

### Post by Lars Noodén on 2015-02-08
If you can connect to SSH via the LAN then that part is all set and the questions are with either your modem or your ISP's network.  

Do you have to explicitly open port 13358 on your modem?  Forwarding might be a two-step process on your model.  Just a guess since i don't have that model.  Another guess might be that your ISP happens to block your incoming port.  You can check with an external scanner like [http://canyouseeme.org/](http://canyouseeme.org/) and see if it is blocked or open.

---

### Post by Joris_Bijvoets on 2015-02-08
Thanks for your quick reply. 

With canyouseeme.org I noticed the port is indeed timing out. That's quite strange as it has worked before. 

I just tried to change the port from 13358 to 22 and to 80, but those still don't work.

Maybe I have to contact my ISP tomorrow?

---

### Post by Lars Noodén on 2015-02-08
That would be one option.  Another might be that your modem has to have that port opened explicitly before it will forward anything from the outside.

---

### Post by Joris_Bijvoets on 2015-02-08
I found the problem... thanks for hinting in the right direction. The port wasn't opened correctly. As external port my own ip was filled in, but it should be 0.0.0.0. It's working fine now.

---

