---
title: "Firewall &amp; Anti Virus"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by hedge2211 on 2009-03-14
I have noticed that there are no or i cant find any anti virus or firewall software on ubuntu. Is this because it does not need it as there are no viruses or do i need to install it myself.

---

### Post by ugm6hr on 2009-03-14
Lots of detail scattered throughout this forum, the wiki and the web answering this question.

Essentially:

1. Little need for antivirus.

2. Ubuntu has a built-in firewall (iptables), which is easily controlled using ufw (command-line) or gufw (GUI).

---

### Post by Sealbhach on 2009-03-14
> **hedge2211 said:**
> I have noticed that there are no or i cant find any anti virus or firewall software on ubuntu. Is this because it does not need it as there are no viruses or do i need to install it myself.

As mentioned, no need for anti-virus unless you're running a server which connects to Windows machines (not to protect Linux but so you don't pass on any viruses to the Windows machines). You can install gufw to run your firewall.


.

---

### Post by hostilejosh on 2009-03-14
you could also use firestarter, which i believe is also a GUI for ufw? both are availiable through the repositories.

---

### Post by taurus on 2009-03-14
> **ugm6hr said:**
> 
2. **_Ubuntu has a built-in firewall (iptables)_**, which is easily controlled using ufw (command-line) or gufw (GUI).

Funny that you mentioned a build-in firewall, iptables, because I made that statement one time and one person jumped in and claimed that you must install firestarter if you want to install a firewall on your machine.

---

### Post by Sealbhach on 2009-03-14
> **taurus said:**
> Funny that you mentioned a build-in firewall, iptables, because I made that statement one time and one person jumped in and claimed that you must install firestarter if you want to install a firewall on your machine.

Yeah, I'm still unclear about that. As I understand it, you need to activate it using gufw or Firestarter?


.

---

### Post by DGortze380 on 2009-03-14
> **Sealbhach said:**
> Yeah, I'm still unclear about that. As I understand it, you need to activate it using gufw or Firestarter?


.

nope. just change the rule set on iptables. It's an implicate allow with no rules by default.

---

### Post by ugm6hr on 2009-03-14
> **taurus said:**
> Funny that you mentioned a build-in firewall, iptables, because I made that statement one time and one person jumped in and claimed that you must install firestarter if you want to install a firewall on your machine.

In fairness, I only started telling new users about a built-in firewall after ufw.

iptables may well have been installed as default before then (I know it has been since I started using Ubuntu), but it is beyond me to administer, so I would never suggest it to a new user without a front-end.

I believe Firestarter is no longer actively developed / supported, which is undesirable for security software; hence my use of ufw.

PS: I hope it wasn't me who jumped in to proclaim Firestarter's necessity in my Ubuntu youth :rolleyes:

---

### Post by taurus on 2009-03-14
> **ugm6hr said:**
> In fairness, I only started telling new users about a built-in firewall after ufw.

iptables may well have been installed as default before then (I know it has been since I started using Ubuntu), but it is beyond me to administer, so I would never suggest it to a new user without a front-end.

I believe Firestarter is no longer actively developed / supported, which is undesirable for security software; hence my use of ufw.

PS: I hope it wasn't me who jumped in to proclaim Firestarter's necessity in my Ubuntu youth :rolleyes:

Nope.  It wasn't you.  It was some newbie.  

As far as I know, Linux has been using iptables since real early, even at the beginning, and it is always on as default.  You use firestarter or ufw to configure it, not to activate it.  Before firstarter and now ufw, you would have to open a port by hand from a terminal.

---

### Post by Sealbhach on 2009-03-14
> **taurus said:**
> 
As far as I know, Linux has been using iptables since real early, even at the beginning, and it is always on as default.  You use firestarter or ufw to configure it, not to activate it.  Before firstarter and now ufw, you would have to open a port by hand from a terminal.

OK, so all ports are closed in Ubuntu by defualt? So you would only use gufw or ufw to open a port if you needed to?


.

---

### Post by OrangeCrate on 2009-03-14
ugm6hr - post #8:

> I believe Firestarter is no longer actively developed / supported, which is undesirable for security software; hence my use of ufw.

Though I can certainly appreciate ufw, I still use Firestarter for a couple of reasons...

First, I don't buy the argument that it's obsolete. There's a difference in a finished product not needing to be tinkered with, and a product that is not complete, and is simply abandoned. Particularly with open source software, since we're not tweaking an existing product, to have something new to sell in the open marketplace.

Firestarter is just a GUI to configure iptables, as is ufw, and in a couple of other threads, I've challenged a couple of members here to show me documentation that it's no longer a useful tool, as they profess, at almost a primal scream. They couldn't, and didn't provide any sources to backup their statements.

Personally, I find Firestarter intuitive and easy to use. Configure what you may, and then close it.

The other reason, is that I prefer to control ICMP filtering. I can do that with Firestarter, and I can't with Gufw, unless there's been an update to this, that I'm not aware of:

[https://answers.launchpad.net/gui-ufw/+question/51550](https://answers.launchpad.net/gui-ufw/+question/51550)

Ufw is certainly easy to use, but so is Firestarter, and Linux is all about choices anyway, isn't it?

Edit:

Forgot to quote the post I was referring to, and have added the comment.

---

### Post by detroit/zero on 2009-03-14
> **OrangeCrate said:**
> Though I can certainly appreciate ufw, I still use Firestarter for a couple of reasons...

First, I don't buy the argument that it's obsolete. There's a difference in a finished product needing to be tinkered with, and a product that is not complete, and is simply abandoned. Particularly with opensource software, since we're not tweaking an existing product, to have something new to sell in the open marketplace.

Firestarter is just a GUI to configure iptables, as is ufw, and in a couple of other threads, I've challenged a couple of members here to show me documentation that it's no longer a useful tool, as they profess, at almost a primal screem. Personally, I find Firestarter intuitive and easy to use. Configure what you may, and then close it.I also continue to use firestarter because of its' ease of use. I've tried gufw, and I think firestarter has more options and offers more control, personally. Of course, neither of them compares to just learning how to use iptables in the terminal.

> **OrangeCrate said:**
>  The other reason, is that I prefer to control ICMP filtering.+1 on that issue, and as far as I remember, UFW doesn't have options for that.

---

### Post by ugm6hr on 2009-03-14
> **OrangeCrate said:**
> Firestarter is just a GUI to configure iptables, as is ufw, and in a couple of other threads

True.

I don't have hard evidence to support my stance, but consider the following:

iptables continues active development, but Firestarter has discontinued active development.  Hence, at some stage, it is conceivable that the *finished product* Firestarter will be incompatible with the current iptables.

Would that time be apparent for someone using Firestarter?  I don't know.  Is this even a possible scenario?  I don't know.  Does it matter?  I don't know.

My concern is that "I don't know" is unacceptable for security software.  But as you say, it is all about personal choice; you pays your money, and you takes your pick.

Ref: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=iptables](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=iptables) (different version numbers for successive Ubuntu versions)

---

### Post by OrangeCrate on 2009-03-14
^,

There's really no argument from me on the issue, I'm just stating an alternative position.

For me personally, when someone definitively defines the "I don't know", I'll be delighted to take another look at my decision to use Firestarter. There is, however, a fine line between "I don't know", and the spread of FUD, and that's something I try to avoid when I post here.

Until then, you're right, it's my choice. As I stated in my earlier post, gufw doesn't completely do what I want it to do anyway, so using it is a moot point for me. If at some point I can toggle ICMP filtering at will, I'll probably switch over to gufw.

But, until then, I see no reason to not use Firestarter.

---

### Post by Georgia boy on 2009-03-14
Why not just use a hardwired  router with the firewall? I've got my pc hooked up with the router. Did the Shields Up test and pass with flying colors. Complete stealth. Wouldn't that do the trick?
Of course I'm still learning. Just look at some of the questions I ask.;)

Tom

---

### Post by doas777 on 2009-03-14
> **Georgia boy said:**
> Why not just use a hardwired  router with the firewall? I've got my pc hooked up with the router. Did the Shields Up test and pass with flying colors. Complete stealth. Wouldn't that do the trick?
Of course I'm still learning. Just look at some of the questions I ask.;)

Tom

good point. The reason I use a software firewall in addition to a hardware firewall, is to get closer to the application sending/recieving the data. there are lots of apps that i would rather not communicate with the internet, but if I allow :80 traffic, the router has no idea that it is from an untrusted application. If a trojan on my host phones home, my router will do nothing to stop it; that opportunity has already past once the packet is sent. Some routers attempt to use deep packet inspection to analyze application layer information, but they are SLOOOOOOOw. 

With a software firewall i can control communications on an application by application basis. in more sophisticated systems, software firewalls also integrate into host intrusion detection systems so that app activity can be analyzed and changes to the firewall can be made in realtime, to adjust to the current situation. it's really kinda kewl.

another potential reason is that you have opened certian ports on your firewall for access, and you don't want a hacker to abuse that to identify other reachable services (though you should always directly target your forwarded ports...). 

have fun,
franklin

---

### Post by presence1960 on 2009-03-14
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

nothing else need be said, read this and all discussion is moot

---

### Post by bootneck02 on 2009-03-15
Hi guy's I am a very new newby having only run Windows XP and Vista and got fed up with having to pay for apps to clean and keep my PC's safe from infection. I have put on the free AVG Ubuntu antivirus and have a Netgear router with a firewall but would feel safer with a software firewall. One of the things I am finding difficult with Linux is the language other users use so could someone please in simple terms what GUI and iptables are and what they do.:redface:Sorry about having to ask but I am only a home user and Linux is a whole new world to me, oh yes do I need a fire wall.

---

### Post by Sidewinder1 on 2009-03-15
Bootneck, WELCOME to ubuntu. Please see the link above your post as it should answer most of your questions and concerns. "GUI" is simply an acronym for Graphical User Interface, which allows you to work in a point and click environment (window) as opposed to the "CLI", (Command Line Interface). HTH and again welcome.
Side

---

### Post by oldos2er on 2009-03-15
iptables is your software firewall. If you are only a "home user" behind a hardware firewall you probably won't need to change anything, but if you do there is gufw and Firestarter.

---

