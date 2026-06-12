---
title: "Is it possible to have more than one SSH port?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by antdgar on 2009-07-14
Hey,

I know port 22 is used for SSH. However, let's assume I'm on a network that blocks port 22, but I still need to SSH into my server.

Is it possible to configure my ubuntu server to accept SSH connections on 22 AND 443? (would this break SSL? If so, are there other ports which have have a high probability of not being blocked, say on a college network...)

Basically, can I configure my server to listen on port 22 and a different port number? And how could I do this?

---

### Post by vruum on 2009-07-14
Do you need port 22? it's pretty easy to have ssh listen on another port, I'm not sure you can have it listen on two different ports though. but if it's just a matter of port 22 being blocked you could just move to a different port.

---

### Post by wojox on 2009-07-14
Look here:

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

---

### Post by wizard10000 on 2009-07-14
I'd be careful.

Not saying you're trying to do anything ignorant like I did but I almost became unemployed several years ago for pulling a trick like this.

Assuming this is your employer's network they're blocking port 22 for a reason.  You may very well still get caught because the firewall will report an SSH protocol being used on a nonstandard port.

If you don't own the network maybe it'd be a good idea not to try to circumvent network security.

---

### Post by antdgar on 2009-07-14
That webpage doesn't help. Also it isn't my employers network. In fact is it nobody's network, purely theoretical. I just DONT want to be without my server just incase a friends networks, public access point, school, college decides to block port 22... when I'm in desperate need to access my server :)

I need both 22 and 443. Not just one.

** It says plural... 'ports' here in SSHD_config:**

[IMG]http://i187.photobucket.com/albums/x268/antdgar/Picture1-65.png[/IMG]

I just need to know how to write it... eg. does it need to be 'port 22, 443' or 'port 22 443'

I cannot afford to be locked out of the server... so I cannot just try blindly :P

---

### Post by vruum on 2009-07-14
you can have two "port lines, like:
Port 22
Port 443 

but, as wizard1000 says, maybe there's a reason they're blocking port 22?

---

### Post by antdgar on 2009-07-14
> **vruum said:**
> you can have two "port lines, like:
Port 22
Port 443 

but, as wizard1000 says, maybe there's a reason they're blocking port 22?
Yeah maybe. But I just want to be safe knowing I can access my server.

How can I 'reload' the file now, or can I just restart? Because it's still not accepting SSH connection on 443?

---

### Post by wojox on 2009-07-14
```
sudo /etc/init.d/ssh restart
```

If you had taken time to read the page you could have figured it out.

---

### Post by Hospadar on 2009-07-14
You could also probably set up an iptables rule to forward whatever port you want to port 22, although if you can just have ssh listen to both ports, I'd say that's a better way to go.

---

### Post by antdgar on 2009-07-14
thanks, it works :D

---

### Post by lovswr on 2009-07-15
posted in wrong thread

---

