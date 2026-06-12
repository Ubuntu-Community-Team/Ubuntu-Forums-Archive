---
title: "SSH Over Internet Fails"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by Raptor45 on 2008-06-24
I've got ssh working over the local network, but if I try to connect over the internet it fails. The router DMZ is set to the server computer.

Any ideas?

---

### Post by wormser on 2008-06-24
Directions to port forward your router should be here: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by Raptor45 on 2008-06-24
As I said, I set up the DMZ.

---

### Post by wormser on 2008-06-24
I am no networking expert, but you should use port forwarding and not DMZ.  Read [this]("http://www.homenethelp.com/web/explain/port-forwarding-dmz.asp").  One thing you can do is use nmap to see if the port is open.

---

### Post by ujwols on 2008-06-24
Can you explain in detail what all steps that you followed ?
Starting from obtaining host services .. You might be missing some step. And also can you explain your hardware setup like how many level of router do you have because for my case i have an ADSL router which is connected to wireless router and the wireless router in turn is connected to my PC.. So in my case I have two level routers is it the same for you ???

---

### Post by shad0w_walker on 2008-06-24
Can you post an error or the details of what happens when you try to connect over the internet? It fails is a little vague.

---

### Post by ujwols on 2008-06-24
Btw.. DMZ would do ..Port forwarding is not Mandator..But Port Forwarding is obviously a better choice because of security reasons.

---

### Post by Raptor45 on 2008-06-24
I did not intend to leave the DMZ on permanently, just used it to eliminate that as a source of error.

Got a pretty basic setup, just cable modem and wireless linksys router.

By fails I mean times out.

I was originally trying to set up a remote desktop connection. I had it working about a year ago, but when I tried to set it up again it could also only connect locally. I then tried to do an ssh connection, which also won't connect.

To connect I've just been using my public IP on port 22, although I've also tried with setting ssh to a different port. It only ever works locally.

---

### Post by Raptor45 on 2008-06-24
Solved the problem on my own.

I have a Linksys WRT54G, and it was blocking the connection.

To fix I had to disable "Filter Internet NAT Redirection" under "Security">"Firewall".

---

