---
title: "SSHing into my computer at home on a network."
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by Nebetsu on 2008-03-15
Ok. I want to use SSH to connect to one of my computers on my network. The problem is, since they all share the same IP address, I'm not sure how to connect to the one computer specifically.

---

### Post by kevdog on 2008-03-16
Each one of your computers on your LAN needs a static Local IP address, and then you need to port forward from your router a specific port to each computer.  Each computer needs to run a ssh daemon listening on a different port.

---

### Post by Nebetsu on 2008-03-16
I don't think my room mates would appreciate messing around with their computers... >>

---

### Post by kevdog on 2008-03-16
Well, just do it to your own then.  Just a question, when you are referring to SSH, are you just talking about computers from inside the same network, or connecting remotely from outside the local network?

---

### Post by Nebetsu on 2008-03-16
Remotely from outside the local network

---

### Post by kevdog on 2008-03-16
Yes, you'd be best assigning your local computer a static IP address, running the ssh daemon on a different port other than 22 (to avoid confusion with other computers), opening up the firewall (or modifying the iptables manually) on the selected port for incoming traffic, port forwarding the selected port on the router to the ssh server, and also if your router isnt assigned a static IP address by the university or ISP, getting an account with noip.com or dyndns.com so you could access your router by name rather than IP address, if the IP address of the router periodically changes.  Sounds like a lot, but its actually very easy once you go through the exercise once!

---

### Post by elcasey on 2008-03-16
You can set up port forwards in your router's firmware. Connect to your router's web interface, forward outside port 1500, for example, to inside port 22 on the static IP of your PC. 

Then to connect from outside your network you just do "ssh -p 1500 [email]user@ssh.dynamicaddress.com[/email]" where you will obviously subtitute the domain name for whatever your public IP is or, easier, the domain name supplied by a dynamic DNS service such as DynDNS or No-IP.com.

I have five machines on my local network set up this way.

---

