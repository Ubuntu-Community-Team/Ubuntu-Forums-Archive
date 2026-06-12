---
title: "I'm confused About Firewall Distros and Server"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2010-10-23
Hi guys I'm a die hard Ubuntu guy all my computers run using ubuntu I love it. Ubuntu have solved my almost every problem but now I've run it to a new one.

I want to build a internet gateway with good firewall integrated so I googled it now I'm confused what are these firewall Distros ex- IPFire, Smoothwall, IPCop what the hell do they do.

Is it enough I run Ubuntu server with squid or do I need one of above I'm really tangled up.

Please can some help me thank you in advance.

And also can some recommend a distro from the list here.

1. Ubuntu Server 10.04 + Squid
2. IPFire
3. IPCop
4. Smoothwall

Also need to tell you guys this to be used at our company to control our ignorant user who doesn't listen to Admins like us who are trying to make their life's easier.

---

### Post by MooPi on 2010-10-23
You don't need to but I run Smoothwall and use it to limit what my system can access. I didn't really need it but I wanted to learn and this gave me an opportunity to explore the firewall interface. It's also fun to look at the log and view the packets that are rejected and from where. Smoothwall is easy to work with but if my power goes out I generally have to reload and reset my preferences. No UPS. Firewalls are probably best suited for enterprise deployments .

---

### Post by sandyd on 2010-10-23
> **MooPi said:**
> You don't need to but I run Smoothwall and use it to limit what my system can access. I didn't really need it but I wanted to learn and this gave me an opportunity to explore the firewall interface. It's also fun to look at the log and view the packets that are rejected and from where. Smoothwall is easy to work with but if my power goes out I generally have to reload and reset my preferences. No UPS. Firewalls are probably best suited for enterprise deployments .

hardened linux + selinux + smoothwall is better :P
Sadly, I only have hardened Linux (kernel) + selinux

---

### Post by Gone fishing on 2010-10-23
Just installed pfsense on a old box to make firewall. Pfsense is FreeBSD based you do the basic setup using a monitor keyboard and mouse then the rest is setup using a very good web interface.

Very cool firewall solution nice graphs and everything but not squid etc it just a firewall.

Ubuntu server and squid is good - I think webmin makes things a lot easier. There is also a tool to set up the iptables as a firewall in webmin

---

### Post by sadaruwan12 on 2010-10-24
Is there a GUI tool that we can use to configure SQUIDE ?

---

### Post by sandyd on 2010-10-24
> **sadaruwan12 said:**
> Is there a GUI tool that we can use to configure SQUIDE ?

webmin

---

### Post by Gone fishing on 2010-10-25
OK screenshot of webmin

---

### Post by nlsthzn on 2010-10-25
I have basically tried a number of the Firewalls OP mentioned (but alas because I am trying to turn my laptop into a router and one of my NIC is wireless they don't want to play)...

However, in my searchings I would have to suggest you check out Untangle ([www.untangle.com](www.untangle.com)) if I could get it to work with my hardware I would definitely be running it (for now I am just using 10.04 Desktop, hey its a home network and UFW should be enough for me :D)

---

