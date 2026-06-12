---
title: "[SOLVED] iptables forwarding"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by LRT on 2007-11-21
i need to know how i can forward all internet traffic from eth0 to eth1 (two nics on the same machine) using iptables. i'm not very familiar with iptables, but i know this can be done fairly easily. could someone show me how? thanks :)

---

### Post by LRT on 2007-11-25
anyone who could help me would be wonderful. i'm a slow learner, and iptables are really not by strong suit. :( thanks.

---

### Post by IamAcoconut on 2007-11-26
I was too lazy to learn iptables, I've been using Shorewall. This might be a slight overkill if you want your local (not remote) machine to act as a router, but I can't help directly with iptables, and I've been satisfied with Shorewall's performance, since I installed it more than a year ago on my home gateway.

Oh, BTW: [http://easyfwgen.morizot.net/gen/](http://easyfwgen.morizot.net/gen/)

---

### Post by Rick Z on 2007-12-03
Hi IamAcoconut,

I have been want to setup my ubuntu to run as router/gateway, but I wasn't able to.  

I have 2 nic installed.  I am able to setup the dhcp server, assign internal ip address, generate new ip when login to my ubuntu router, and able to login with ssh & webmin tcp port, but I am not able to access internet or outside of this router once I am behind the ubuntu router.  can you please show me how to forward my loc zone to access internet or any other ports?

Thank you!!!

Rick

---

### Post by IamAcoconut on 2007-12-04
I can only advise you to use Shorewall, because I know how it works, and wise people say it works  well ;)

First, a few questions:
- Are running a DHCP for your local network on the gateway?
- Do you have a server (not the desktop) edition installed on the particular PC?
- Are you able to access the net from the gateway[-to-be]? 
* If it's the server you may try to ```
ping 208.67.220.220
``` which is OpenDNS service, that you can also write to your /etc/resolv.conf instead of your ISP's dns servers.


Start here [http://shorewall.net/two-interface.htm](http://shorewall.net/two-interface.htm) and here: [http://shorewall.net/FAQ.htm#faq15](http://shorewall.net/FAQ.htm#faq15)
- On Gutsy you might need to tick/uncomment the two [already existent] repositories in synaptic/sources.lst if you can't find shorewall in your repos.

Note: 
- You can use Webmin to mess with Shorewall. You can easily verify and apply your config to the firewall without typing comands. 
- Use manpages (i.e. man shorewall-interfaces) whenever you're in doubt. They might be especially helpful if your shorewall doesn't install the template files for (i.e. for two-, three- NIC configuration etc.) as did the debian version I once used. Couldn't find those files on Ubuntu. It might have been my dumbness tough ;)

---

### Post by LRT on 2007-12-06
i posted my question on linuxquestion.org

it seems that all i needed to do was this command:

```
echo '1' > /proc/sys/net/ipv4/ip_forward
```

and to make sure /etc/dhcp3/dhcpd.conf was correctly configured.

[http://www.linuxquestions.org/questions/linux-networking-3/iptables-forwarding-602481/]("http://www.linuxquestions.org/questions/linux-networking-3/iptables-forwarding-602481/")

---

### Post by Rick Z on 2007-12-06
I got it to work now...  :)  I follow up by reading all the good documentation from Shorewall Website.  I saved my current shorewall configuration by the following command.

#shorewall save

Thank you for pointing out for me.

Rick

---

