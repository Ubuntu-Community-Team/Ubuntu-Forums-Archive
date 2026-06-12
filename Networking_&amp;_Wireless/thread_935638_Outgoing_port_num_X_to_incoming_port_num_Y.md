---
title: "Outgoing port num X to incoming port num Y"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by TreeFinger on 2008-10-01
My goal is to have an obscure port number open on my firewall for incoming SSH connections.

I plan on connecting, for the most part, while I am on my university's campus. 

My obstacle there is that they will not open an obscure outgoing port for me to use.

Is there a way for me to use outgoing port 22 but connect to my SSH server on port 8234 (example).

I will be using Putty ssh client.

---

### Post by TreeFinger on 2008-10-02
bump

---

### Post by superprash2003 on 2008-10-02
possible.. certain routers have that functionality where you can assign external ports and internal ports..

---

### Post by TreeFinger on 2008-10-02
> **superprash2003 said:**
> possible.. certain routers have that functionality where you can assign external ports and internal ports..

I'll be going through 2 different firewalls. I'll be leaving firewall A, which I have no control over and entering firewall/router B, which is my own router using IPTABLES.

Is it possible to leave router A on port 22 and enter router B on port 27893

---

### Post by TreeFinger on 2008-10-02
bump

---

### Post by fedoraboy on 2008-10-02
I'll go out on a limb and say no.  Not unless there is a router in the middle that you control that can manipulate this.

That is like saying "I want to knock on my neighbor's door, but when they open it, step into my house."

You could do some stuff to limit things though... If you know the IP address (or range) you would be coming from, you could limit the ssh server to only accept from that IP (or range).

---

### Post by TreeFinger on 2008-10-02
> **fedoraboy said:**
> I'll go out on a limb and say no.  Not unless there is a router in the middle that you control that can manipulate this.

That is like saying "I want to knock on my neighbor's door, but when they open it, step into my house."

You could do some stuff to limit things though... If you know the IP address (or range) you would be coming from, you could limit the ssh server to only accept from that IP (or range).

Yea, I'm guessing that is what I will have to do..

I don't understand why the person running the firewall is fine with having port 22 outgoing open but not fine with some obscure port number lol. Does it make any sense to you? I asked if they could open an obscure outgoing port and they pretty much said no.

---

### Post by TreeFinger on 2008-10-02
> **TreeFinger said:**
> Yea, I'm guessing that is what I will have to do..

I don't understand why the person running the firewall is fine with having port 22 outgoing open but not fine with some obscure port number lol. Does it make any sense to you? I asked if they could open an obscure outgoing port and they pretty much said no.

lookin for an explanation for this... bump

---

### Post by superprash2003 on 2008-10-03
you would have to ask that guy for the explanation..cause its safer not to use standard ports..

---

### Post by kevdog on 2008-10-03
Yes its possible to do what you want.  I'm not sure what your problem is or specifically what the problem is as related to your discussion.

---

### Post by TreeFinger on 2008-10-03
> **kevdog said:**
> Yes its possible to do what you want.  I'm not sure what your problem is or specifically what the problem is as related to your discussion.

My school is only allowing me to SSH to my home computer from port 22.. I would not like to have port 22 open on my firewall as this leads to many attacks.

---

### Post by vociferous666 on 2011-06-21
you could set up an old linksys 54g running dd-wrt at a friends house, 
ssh into that on port 22, 
then once in, ssh through your home router on 8726 or whatever,

you could even simplify your installation on the ssh endpoint by translating incoming port 8726 to local port 22.

the only configuration would be in the routers :)

i know it seems a bit complicated but its what i would be willing to go through for security. plus the added benefit of TWO ssh logins plus a very basic honeypot to break through if the attacker doesnt know your obscure port already.

---

