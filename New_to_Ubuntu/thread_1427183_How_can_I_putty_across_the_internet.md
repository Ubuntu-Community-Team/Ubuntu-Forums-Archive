---
title: "How can I putty across the internet?"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-11
I want to be able to access my bash shell from across the internet. How can I make this happen on Ubuntu?

---

### Post by viralmeme on 2010-03-11
> **TurnOfTide said:**
> I want to be able to access my bash shell from across the internet. How can I make this happen on Ubuntu?
Try SSH ..

[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

---

### Post by TurnOfTide on 2010-03-11
Also the client will be a windows machine, do I just run a port of PuTTy for windows to connect?

---

### Post by muteXe on 2010-03-11
i think ssh is on port 22, and putty IS for windows..

---

### Post by NertSkull on 2010-03-11
Just make sure you secure your machine.  That you have a good password to connect.  Opening up SSH (especially if you leave default on port 22) allows for people to brute force attack your computer. 

I would actually highly suggest using ssh-keys to connect without a password and turn off password log-in.

Thats all pretty easy to do, let us know if you need help.

---

### Post by Mighty_Joe on 2010-03-11
How do you connect to the internet?  You will probably have to do some [port forwarding]("http://portforward.com/") to get the incoming traffic to your computer
You will have to know your IP address.  Most residential ISP's will use DHCP, so your IP will change from time to time.  I got around this by registering a domain name and using a [Dynamic DNS]("http://en.wikipedia.org/wiki/Dynamic_DNS") service to keep updating the IP the domain points to.

---

