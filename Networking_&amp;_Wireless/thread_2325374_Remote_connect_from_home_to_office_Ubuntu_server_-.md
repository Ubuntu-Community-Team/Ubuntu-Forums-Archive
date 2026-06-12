---
title: "Remote connect from home to office Ubuntu server - best tool"
date: 2016-05-21
forum: Networking &amp; Wireless
---

### Post by jamarsh123 on 2016-05-21
At present, I am using SSH to connect to an Ubuntu server but from within the network, ie same router. I would like to be able to connect to the same server from home.  The server has no gui, so I would just be connecting to the terminal. Is "ssh" the best tool or is there something better? If ssh, how do I connect to and get through the router?

---

### Post by papibe on 2016-05-21
Hi jamarsh123.

If the server is not in your control, you need to ask both permissions and instructions to the IT people.

If permission is not the problem, my guess is that they'll give you some of these alternatives:
[LIST]
[*]VPN access to the office network.
[*]a specific IP or domain to connect from outside the network.
[*]the above plus a specific port.
[*]
[/LIST]
ssh is the best alternative for remote connection to a server. Note that there are common practices to secure a server and ssh connections, but usually they are the responsibility of the people who admin the server. In your side, I'd recommend creating a pair of ssh keys ([here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")'s how).

Hope it helps. Let us know how that goes.
Regards.

---

### Post by jamarsh123 on 2016-05-22
Thanks for the reply. I am in control of the server and just need to be able to access from home or some other location. Is another application required or just some modifications to the ssh application/and or router?
thanks
jamarsh123

---

### Post by papibe on 2016-05-22
If the server has its own public IP, you can connect directly.

If not, a simple solution is to forward a port in the office's router to port 22 on the server. This way you can access the server like this:
```
ssh -p12345 youruser@publicIP
```
where 12345 would be port forwarded on the router, youruser your server's username, and publicIP the public IP of the office.

Since this put your server available to the rest of the world, I'd recommend:
[LIST]
[*]setting up ssh keys
[*]disable password login
[*]disable root login
[*]configuring iptables to close all other ports, and restrict login attempts
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by walttheboss on 2016-05-23
All you have to do is login to your router from the LAN.  Find where your router configures port forwarding (sometimes called virtual server)  Then send port 22 to the server lan ip address.

---

### Post by jamarsh123 on 2016-06-08
> 
If the server has its own public IP, you can connect directly.

If not, a simple solution is to forward a port in the office's router to  port 22 on the server. This way you can access the server like this:
     Code:

     ssh -p12345 youruser@publicIP 
where 12345 would be port forwarded on the router, youruser your server's username, and publicIP the public IP of the office.


This did the trick; thanks for your help

---

### Post by jamarsh123 on 2016-06-08
I don't know how to do it, but this thread can be marked as "solved."

---

### Post by oldos2er on 2016-06-08
You may mark the thread 'Solved' using the Thread Tools drop-down menu at the top of the page.

---

