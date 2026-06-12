---
title: "Help to firewall-protect my Ubuntu"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by oingk on 2010-03-12
HI

I want to firewall protect my Ubuntu. I installed Ubuntu (9.10) three days ago, I'm still a beginner.

I know it's not considered very crucial to firewall-protect linux systems, but I connect a lot to wireless internet connections, sometimes even unsecure ones, so I want to be a bit safe.

I've heard there's a firewall by default on Ubuntu. Is this firewall good? Is so, how can I enable it?
If it's not good, please let me know of a good one.

thanks

---

### Post by mbzn on 2010-03-12
By default Linux's IP-Tables(like a firewall) blocks all incoming traffic unless requested. This (to my understanding) is by far better than any (firewall in windows). A firewall in Linux would then make IP-tables 'weaker' if used incorrectly. For home use it is completely unnecessary. Firewalls is used on servers that needs to accept incoming traffic.

P.S. Don't worry 'Linux is not Windows' you're safe

---

### Post by oingk on 2010-03-12
OK I think I understand, thanks

---

### Post by Shazaam on 2010-03-12
To add...
If you want a gui app for tweaking parts of iptables/netfilter (Ubuntu's "firewall") install gufw through the Synaptic Package Manager. But it's not really an issue unless you need to open specific ports for things like a web server or networking apps like samba. Read up as much as you can before punching holes in iptables.
Here are a few links for you...
[https://help.ubuntu.com/9.10/keeping-safe/C/firewall.html](https://help.ubuntu.com/9.10/keeping-safe/C/firewall.html)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

---

### Post by oingk on 2010-03-12
shazaam, thanks

---

### Post by strumusa on 2010-03-14
I just installed Firestarter yesterday..It is free sw offered with ubuntu..Go to Applications-->sw center-->sys. tools....It's better than nothing.

---

### Post by J V on 2010-03-14
*sigh*

You don't need it
Firestarter is more of a security risc than a fix

See premade post for so many of these:
> **Firewall**
Ubuntu comes with a fantastic firewall known as iptables. It is inactive by default, because no applications are "Listening" to the ports (Doorways) on your computer anyway, so there is no need for a firewall.

Iptables is actually very hard to configure, you need to edit configuration files, know the program, its just much more advanced. Luckily, there are tools that make this easy.

The most often advised firewall interface is "Firestarter", but nowadays its a bad idea to use it. It hasn't been developed for ages now, and because ufw (A command line configuration tool) is installed, Firestarter will conflict with already running services.

On top of that, while it runs, it runs as root, so if someone were to exploit a vulnerability in Firestarter, it would give them complete access to your system.

The current interface suggestion is "[gufw]("apt://gufw")" (Click to install) which, once again, is not a firewall, but a means to configure the default firewall.

---

### Post by strumusa on 2010-03-14
> **J V said:**
> *sigh*

You don't need it
Firestarter is more of a security risc than a fix

See premade post for so many of these:

Well, underneath Firestarter is something called 'Firewall configuration", which allows you to configure ufw firewall...I just installed that directly from sw center.  I now see the icon under admin., but don't understand how to setup rules very well.  I think Firestarter is kool in that you can see real-time firewall event monitoring showing intrusion attempts as they happen.  Also, to and from ip's for active connections.

---

### Post by nitstorm on 2010-03-14
Don't worry about a virus infection in Linux brother. Been using it for a couple of months now and the most surprising thing is there is never a virus infection. and even if a virus does get into ur system somehow it does not affect it coz this ain't Windows :D if u are so worried about protecting ur system, try 
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

or if u are jus plain paranoid or too worried about rootkits or something try rkhunter  ( it's an app, u'll be able to find it in the repos)

---

### Post by J V on 2010-03-14
> **strumusa said:**
> Well, underneath Firestarter is something called 'Firewall configuration", which allows you to configure ufw firewall...I just installed that directly from sw center.
Never heard of that... still it runs as root and hasn't had an update in forever :)

---

### Post by cusinmex on 2010-03-14
Linux is secure as secure can get.

The chances of something happening
like a virus or something of that nature
is very slim.

I don't know why you would want to use a firewall..

but anyways
there's firestarter for that.:p

---

