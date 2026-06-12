---
title: "Do I need a Firewall?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by jozmoz on 2009-01-18
Hi,
Do I need a firewall?  Are there people out there trying to gain access to ubuntu operating systems? A friend of mine reckons I need one. What do you think?

Thanks for any replys.

---

### Post by theozzlives on 2009-01-18
You have a firewall, it's called IPTables.

---

### Post by bryncoles on 2009-01-18
short answer: probably not. 

long answer: you already have one, its called UFW (uncomplicated firewall), and it governs the IP tables - how your computer interacts with the internet. if you're using the standard ubuntu install with nothing extra installed, then you have nothing listening at the internet, so no changes need to be made. 

see these links for further useful information though: 


configure the firewall: 
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

ubuntu security tips:
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

secure firefox:
[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by mcduck on 2009-01-18
No. The default install of Ubuntu doesn't have any running services that would respond to incoming connections from network. Because of this a firewall is not needed.

However, if you install any such services, like a web server, you should set up a firewall. In that case I recommend using ufw, or it's graphical version Gufw.

Theozzliveses post is, in some ways, correct, and then again not. Linux includes all the tools and features needed to create a firewall (netfilter/iptables), but it doesn't do anything by default. You have to give it some rules to work with. Pretty much every Linux firewall is just a tool that is used to create and manage these rules, but you could also do it by hand or create your own script to handle the firewall.

Ubuntu includes ufw (simple command-line based firewall tool) by default, but it isn't running unless you activate it.

---

### Post by bryncoles on 2009-01-18
+1 mcduck.

the first link i posted is a guide to setting up UFW from the dreaded command line. or you can install GUFW from the repo's (though i managed to completely block my mothers xubuntu from the internet by using GUFW instead of the command line! its easy to fix though - i just turned GUFW off again!)

---

### Post by OrangeCrate on 2009-01-18
> **jozmoz said:**
> Hi,
Do I need a firewall?  Are there people out there trying to gain access to ubuntu operating systems? A friend of mine reckons I need one. What do you think?

Thanks for any replys.

In addition to all the fine advice already given, here's a good initial read on Ubuntu security...

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

There are links to additional resources on that page too.

:)

---

### Post by gn2 on 2009-01-18
> **bryncoles said:**
> ubuntu security tips:
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

You might want to change that link for [this one]("http://ubuntuforums.org/showthread.php?t=510812")?

---

### Post by bryncoles on 2009-01-18
> **gn2 said:**
> You might want to change that link for [this one]("http://ubuntuforums.org/showthread.php?t=510812")?

good call, they seem to be the same article, but yours is from the original author! its better practice to go to source!

---

