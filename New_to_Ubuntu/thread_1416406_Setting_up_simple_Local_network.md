---
title: "Setting up simple Local network"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by rikilshah on 2010-02-26
Hi there.I am having 10 machines,would be running ubuntu 9.10.Now I want to make LAN with server authenticating users with giving some hard disk space on server.
I am confused between whether to install ubuntu server edition or to use samba for the same.Network would be strictly restricted to only 10 machines so I am leaning towards Samba,but I don't know if it is completely possible to make such network using Samba.It would  be great if someone can guide me through the process.[LEFT][/LEFT]

---

### Post by yrnajraven on 2010-02-26
hello there mate . .we have same situation right here, .im planning to setup 5 ubuntu units 2 months from now, but im totally new to linux or ubuntu, but im loving what im learning along the way,.. 
Thus i decided to stay here in ur post, while awaiting for knowledgeable ones to reply here ..

---

### Post by pbpersson on 2010-02-26
I have never done this, but Google the following phrase:

"Samba as a Primary Domain Controller"

That will get you started.  At least once you read some of the articles you will have a better idea of where you are going

---

### Post by Kakers on 2010-02-26
Haven't really touched Ubunu server before, but I have had some experiance with CentOS as a server solution. You could set up a CentOS server with a samba share and also use it as a firewall and even a DHCP server :D

But you may not want to run too many things on one box... however if it is only for 10 computers it shouldn't break a sweat.


Here are some links that may help you:
Samba - [http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-samba-configuring.html](http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-samba-configuring.html)
Samba - [http://crazytoon.com/2007/05/22/samba-how-do-you-install-and-set-up-samba-in-linux-redhat-enterpriserhel-centos-fedora/](http://crazytoon.com/2007/05/22/samba-how-do-you-install-and-set-up-samba-in-linux-redhat-enterpriserhel-centos-fedora/)
DHCP - [http://www.linuxreaders.com/2009/04/23/dhcp-server-on-centos/](http://www.linuxreaders.com/2009/04/23/dhcp-server-on-centos/)
Iptables (firewall) - [http://www.cyberciti.biz/faq/rhel-fedorta-linux-iptables-firewall-configuration-tutorial/](http://www.cyberciti.biz/faq/rhel-fedorta-linux-iptables-firewall-configuration-tutorial/)

At my place of work we use CentOS for all our servers and Ubuntu for our desktops :o Anyway... hope this helps.

---

