---
title: "SSH on Odroid XU4"
date: 2018-01-06
forum: Networking &amp; Wireless
---

### Post by teckthekid on 2018-01-06
Hello all,

I am using ubuntu on my Odroid XU4 board and it works great. 
I have a issue with SSH from out side my network. 
It works fine from inside, I set up port forwarding on my router but I still can’t connect. 
Are any settings in ubuntu that might stop it?

---

### Post by Hadaka on 2018-01-06
Hi, how EXACTLY are you formatting your command ?
*Should be..From 'offnet'...'outiside'... the lan
     ```
ssh -p port# user@public IP
``` 
or if default port 22..
     Code:
     ```
ssh user@public IP
``` 
*Verify the port is set to "listen"
     Code:
     ```
cat /etc/ssh/sshd_config
``` 
*To find public IP
     Code:
     ```
whatismyip.com
``` 
*Router.. Port forward "port" to "server" ip
     Code:
      ```
Port Foward  "2222" -> "192.168.1.X"
``` 
*This only works from OUTSIDE your network.

---

