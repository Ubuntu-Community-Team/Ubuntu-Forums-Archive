---
title: "ssh from linux to macbook not on LAN"
date: 2016-01-20
forum: Networking &amp; Wireless
---

### Post by gilly2 on 2016-01-20
Hi everyone! I have ubuntu on my home pc and I want to be able to ssh to a macbook.  When they are both on the same wifi network it's no problem (I just looked at sharing under settings and it said ssh [email]user@blahblah.local[/email] or something), but how do I  ssh to the mac when it's outside the lan? I heard about port forwarding but I don't have access to the router. Thanks in advance!

---

### Post by cariboo on 2016-01-21
It depends on where the macbook is, at minimum you would need the macbooks ip address. As long as it isn't a non-routable address eg:  10.0.0.0 - 10.255.255.255, 172.16.0.0 - 172.31.255.255, 192.168.0.0 - 192.168.255.255 you shouldn't have a problem accessing it.

---

### Post by gilly2 on 2016-01-21
I tried to just plain ssh it with user@ip but it said something about port 22?

---

### Post by Vladlenin5000 on 2016-01-21
Yes, you're right about port forwarding and no, there's no way around it.
You need to tell the other LAN's router to forward requests to the Public_IP:port to the Mac's Internal_IP:port, the internal IP being the one assigned to it in the other LAN, something like 192.168.xxx.xxx. Otherwise the other router can't know where to send the request.

---

### Post by gilly2 on 2016-01-21
What if I don't have access to the router or my laptop travels around and is then in a new LAN? I heard you can set up a VPN? Could you tell me how to do that? Also if it can be done for free that would be good too ;) Thanks.

---

### Post by gilly2 on 2016-01-28
Can anyone please tell me how?

---

### Post by leith98b on 2016-01-28
Setting up a VPN can be done, but it depends on various factors.  Since you said you don't have access to the router/gateway then it seems the port forwarding is out of the question.  I'm assuming you have a private IP address on the Mac, something like 192.168.x.y?

---

### Post by Hadaka on 2016-01-28
Hi, this is the basic set up for ssh  to communicate with a remote computer.
[your laptop] needs to have open ssh server/client software loaded.
[your laptop] can be any where on any lan or network

[mac computer]needs to have open ssh server/client software loaded.
[mac router] needs to port forward request to it's public IP to a port that is forwarded to the mac's lan IP
[mac computer] needs to have its ssh software configured to "listen to" the port you choose to forward.

*Below are the basics of how it works...each line giving more detail in the process. IP addresses and port number are examples only.

[your laptop] ->   ssh -p "a port number"  "computer name" @ "routers public ip" "router-port-forward " to "computer lan IP"

[your laptop] ->   ssh -p 22 mac_computer@mac_router "whatismyisp" The router then port forwards to the mac computer lan IP

[your laptop] ->   ssh -p 22 mac_computer@172.75.34.12  <-mac router public ip ...to find, at mac browser enter "whatismyisp"

[your laptop] ->   ssh -p 22 mac_computer@172.75.34.12  ->mac router port forwards port 22 to mac lan iP "192.168.1.105"

[your laptop] ->   ssh -p 22 mac_computer@172.75.34.12  -> mack computer set to "listen to port 22" in ssh server configuration.

[your laptop] ->   ssh -p 22 mac_computer@172.75.34.12  <- example of complete command.

There are countless articles and tutorials on how this works, I would suggest you do some research to become
comfortable with the basics.
Good luck.

---

### Post by gilly2 on 2016-02-07
Again I dont't have access to the router to set up port forwarding. And yes doesn't every mac have a private ip?

---

### Post by Hadaka on 2016-02-07
Hi, you say "doesnt every mac have  private ip?"
No..they dont. If however they have a router and internet conection then yes they do.
and it is usually the router that assigns that private ip to the computer. and as is most
common, that ip is 192.168.x.x This then means there are millions of computers with the same
private ip address. as in 192.168.1.102 ,The router is assigned a unique IP address by the internet servicve provider.
so if you want to communicate via ssh to a machine not on your lan you must port forward a port to that computers ip.
as in ssh -p 22 gilly2@routers_Public_IP     router portforwards port22 to computer_private_IP       and that computer has to "Listen" to port 22

so,,.,again,,if you dont have access to the router to port forward to the mac.....then you wont be able to ssh to it.

---

