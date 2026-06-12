---
title: "Is Firewall Enough for me?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Revo99 on 2010-03-09
Hello to all,

Thank you in advance for your time. 

I am running Ubuntu Server 9.10 building from the base up with the goal of learning the ins and outs of a linux server. I am new to this but.

I wanted to know firstly what a good firewall configuration tool would be? I want something where I can start with the basics then build into advance features. 

Secondly as it is a server do I need an Anti Virus program. What would you suggest if so.

Cheers,

Revo99 :D

---

### Post by d3v1150m471c on 2010-03-09
It depends on who you ask and what you're trying to do. Firestarter, tripwire, and psad are probably in your alley.

---

### Post by J V on 2010-03-09
NO firestarter... it runs as root, and hasn't been updated in 5 years... put it on your system and its already comprimised...

Like the man said, what are you trying to do?

---

### Post by ukripper on 2010-03-09
ubuntu server has no graphical frontend due to performance difference it makes. Therefore to learn ins and out of linux server firewall, you need to get your hands dirty with iptables or shorewall likes. Excellent tips on iptables here- [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

### Post by 3rdalbum on 2010-03-09
A firewall is probably close to useless, running on a server. A firewall stops incoming connections; now the reason why you're running a server is so that other computers can create incoming connections. If there's something you don't want users to access, then remove it from the server, don't just firewall it.

If you do want a firewall for something, then use UFW to configure it. The suggestion to use Firestarter is a little odd, because Firestarter is a GUI program and Ubuntu Server doesn't come with a GUI. You can install a GUI onto Ubuntu Server, but then you might as well be using Ubuntu Desktop with server packages. Firestarter is virtually unmaintained anyway now, so you might as well avoid it. If you need a GUI firewall configuration utility, use gUFW.

You don't need antivirus. There are no Linux viruses.

---

### Post by Revo99 on 2010-03-09
> **J V said:**
> NO firestarter... it runs as root, and hasn't been updated in 5 years... put it on your system and its already comprimised...

Like the man said, what are you trying to do?

Well I am running Ubuntu 9.10 Server as a home server. Building it from the ground up. As a file/media server. I want to use a GUI based firewall with some sort of wizard. As I have no firewall at the moment. Should I just install.

My networking setup currently is:

Modem/Router attached by ethernet to my Apple time capsule then ethernet to my Server.

I am planning to setup my wireless card instead of ethernet to my server. But need to post a thread about this. 

I should possibly just intsall GUFW.

Help is appreciated.

Thanks

---

### Post by Revo99 on 2010-03-09
> **3rdalbum said:**
> A firewall is probably close to useless, running on a server. A firewall stops incoming connections; now the reason why you're running a server is so that other computers can create incoming connections. If there's something you don't want users to access, then remove it from the server, don't just firewall it.

If you do want a firewall for something, then use UFW to configure it. The suggestion to use Firestarter is a little odd, because Firestarter is a GUI program and Ubuntu Server doesn't come with a GUI. You can install a GUI onto Ubuntu Server, but then you might as well be using Ubuntu Desktop with server packages. Firestarter is virtually unmaintained anyway now, so you might as well avoid it. If you need a GUI firewall configuration utility, use gUFW.

You don't need antivirus. There are no Linux viruses.

Firstly Great to hear from an aussie! Thanks for the advice. I was looking at GUFW just then you posted. Before I could post anything.

The reason I am running a server is to learn about how to operate them. With the intention of moving to a more networking role in the future in. I am currently in a software support. Which has its fair share of networking etc. But not enough time nor permission to experiment.

Would be interested to hear your thoughts

Cheers,

Revo99

---

### Post by 3rdalbum on 2010-03-09
> **Revo99 said:**
> Well I am running Ubuntu 9.10 Server as a home server. Building it from the ground up. As a file/media server. I want to use a GUI based firewall with some sort of wizard. As I have no firewall at the moment. Should I just install.

My networking setup currently is:

Modem/Router attached by ethernet to my Apple time capsule then ethernet to my Server.

Your modem/router probably already contains a firewall that will protect your home network. If this is the case, then running a firewall on the server will be a complete waste of time as it will never see a packet that needs to be blocked (the outermost firewall will block everything).

---

### Post by Revo99 on 2010-03-09
Great I think you are right. I feel a bit stupid now. Attached is a screenshot of what is configured in router.

I installed and removed fwbuilder & firestarter. I think something is wrong now on my server. Because I cant access webmin from my other computer on the network. Where as before I could. :(

Cheers,

Revo

---

