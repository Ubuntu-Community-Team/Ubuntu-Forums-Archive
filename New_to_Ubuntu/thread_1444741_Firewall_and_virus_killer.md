---
title: "Firewall and virus killer"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by mushypeas on 2010-04-01
Do firewalls and virus killers exist for ubuntu please? If so, which are best. I am converting from windows and just want to be "better safe than sorry"

---

### Post by Rex Bouwense on 2010-04-01
Yes.  See

[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

for information on virus.  There is a firewall installed in Ubuntu to activate it download Firestarter.  Enjoy.

---

### Post by spiky001 on 2010-04-01
Firestarter is not supported any more if you want a graphical version of the firewall which is installed get gufw it,s in the resportories

 Google virus on linux it is really not nessesary not like windows, if you share with windows use clam av but for linux is unnessecary

---

### Post by uRock on 2010-04-01
+1 on using GUFW, it is simple and it is great.

Welcome to ubuntu and the ubuntuforums.:D

---

### Post by uRock on 2010-04-01
To learn more on security in ubuntu please read the sicky threads in this link, [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338").

---

### Post by Rex Bouwense on 2010-04-01
> **spiky001 said:**
> Firestarter is not supported any more if you want a graphical version of the firewall which is installed get gufw it,s in the resportories

 Google virus on linux it is really not nessesary not like windows, if you share with windows use clam av but for linux is unnessecary
Firestarter is still in the repositories.  I was unaware that it is not supported.

---

### Post by uRock on 2010-04-01
> **Rex Bouwense said:**
> Firestarter is still in the repositories.  I was unaware that it is not supported.

The last updates to its interface were in 2005. It still works though.

---

### Post by oldsoundguy on 2010-04-01
and you also really do not need the firewall unless you are setting up your own lan and others will be using it, or you are direct through modem to the internet.  
IF you use a router, all of the new models  have a built in firewall that is part of the firmware. Installing the repository firewall is not needed in that case.

---

### Post by mushypeas on 2010-04-02
thanks everyone

---

### Post by HermanAB on 2010-04-02
Howdy,

Just to give you some idea of how it works:
Linux pretty much *is* a firewall.  Cisco router and firewall devices all run Linux.

The Linux 'firewall' function is done by the netfilter kernel module.  It forms an integral part of the Linux network stack - hence my comment above.  Netfilter is configured with a program called iptables.  However, iptables is arcane.  Consequently, there are a zoo of other programs commonly referred to as 'firewall' programs, that implement somewhat more friendly front ends for iptables the unfriendly front end for netfilter.

You don't normally need to run a 'firewall' program.  The default Ubuntu Linux install is already quite secure as is.  However, if you are paranoid, then you could tighten things up a little more and configure netfilter yourself using iptables or something like gufw or firestarter, or shorewall, or monowall, or ipcop, or....

So, I would actually recommend that you do nothing.  Ubuntu is fine as is.  Mucking with iptables while you don't really know what you are doing, will likely cause more problems than it will prevent!

---

### Post by 3rdalbum on 2010-04-02
Every week I reply to two or three messages from people who have installed and attempted to configure firewall configuration programs.

A firewall prevents the programs running on your computer from hearing any incoming connection requests. A default Ubuntu install will not listen to incoming connection requests anyway, so a firewall will not help. In fact, a firewall adds an added level of complexity to your system and yet another thing that you must remember to configure.

In addition, most ADSL/cable modems, and multi-port routers, contain a firewall that prevents your entire network from listening to incoming connection requests from outside your network. In the extremely LIKELY event that you have one of these, then none of your computers needs a firewall.

As for your other question, there are anti-virus programs for Linux, but you don't need them because there are few, if any, viruses that work on Linux these days. You'll probably never get one.

---

