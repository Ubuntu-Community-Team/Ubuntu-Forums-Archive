---
title: "Is there a way to instant message direct connect from PC to PC?"
date: 2015-12-16
forum: Networking &amp; Wireless
---

### Post by DVD-R on 2015-12-16
Hi All,
Does Ubuntu or Linux have any type of method or application to instant message from one PC to another PC over the internet?

Thanks in advance
Got_Ubuntu :-]

---

### Post by chili555 on 2015-12-16
Please check here: [https://help.ubuntu.com/stable/ubuntu-help/net-chat-empathy.html](https://help.ubuntu.com/stable/ubuntu-help/net-chat-empathy.html)

---

### Post by DVD-R on 2015-12-16
Thanks chili555!
It looks like empathy, pidgin etc......all of the standard IM clients utilize some kind of intermediate online server as the hub between the end-point-clients.
So far, I don't see any point-to-point functionality....but I'll be its possible.

---

### Post by sudodus on 2015-12-16
You can use the ancient ***write*** program (if you install openssh-server and log in from the other computer 'as another user').

See ```
man write
```

---

### Post by chili555 on 2015-12-16
> It looks like empathy, pidgin etc......all of the standard IM clients utilize some kind of intermediate online server as the hub between the end-point-clients.I thought that's what you were asking:> instant message from one PC to another PC over the internet

---

### Post by ian-weisser on 2015-12-16
> **DVD-R said:**
> all of the standard IM clients utilize some kind of intermediate online server as the hub between the end-point-clients.

Yes, a central exchange so clients can discover each other.
How can clients across the internet locate each other without a common exchange?

---

### Post by sandyd on 2015-12-16
If you want something GUI, take a look at any client that supports Bonjour/Avahi

Pidgin comes to mind.

---

### Post by DVD-R on 2015-12-22
Sorry.... I should remember that I need to be really precise when asking questions.
I should have mentioned that I know that IM can be done using an intermediate HOST-HUB system.
So sorry!!   PC to PC is just too vague!
The standard IM setup is PC-CLIENT-A to [HUB-IM-SERVER] to PC-CLIENT-B, where the HUB is some server on the internet.
I was hoping I might find a way to IM, lets say.....from my PC at work, directly to my PC at home without the need for any intermediate HUB-IM-SERVER.
Perhaps the best way to do that would be to setup my home PC as a SERVER for instant messaging.
Then one person (who just happens to be located at my home), accesses my home PC (using Pidgin) and my home PC is functioning as an IM server.
And I access my home IM server remotely (using Pidgin). 
Sorry for the confusion!!

---

### Post by ian-weisser on 2015-12-22
I suspect that IM clients (and mail clinets, and VOIP clients, and ssh clients) are designed to talk to hubs, not directly to other clients.
I think your idea to run a private hub is the simplest solution for the situation you describe.

---

### Post by sudodus on 2015-12-22
You can do that with ***write*** :-)

(... and probably with other tools too, but I haven't tried that)

---

