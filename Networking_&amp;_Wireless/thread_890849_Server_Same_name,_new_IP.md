---
title: "Server: Same name, new IP"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by ranthal on 2008-08-15
My server at work was just assigned a new IP address.  When I type the server's name into my browser, ssh, etc it looks for it based on the old IP address.  How do I change this association without rebooting?

I'm sure it's straightforward, just want a chance to learn more about some of the networking in Ubuntu.

---

### Post by dfreer on 2008-08-15
> **ranthal said:**
> My server at work was just assigned a new IP address.  When I type the server's name into my browser, ssh, etc it looks for it based on the old IP address.  How do I change this association without rebooting?

I'm sure it's straightforward, just want a chance to learn more about some of the networking in Ubuntu.

You'll want to check out what service is translating the server name to IP address and update it accordingly. It could be a DNS server, a WINS server, maybe a router that has something like this build in.

If nothing else, you can edit your /etc/hosts file and add the server name with the update IP address. This means though if it ever changes IP again you will need to update /etc/hosts again too.

BTW, I'm pretty sure this wouldn't be a Ubuntu-only problem, unless there's something very unique about the way your Ubuntu machine is hooked up to your network.

---

### Post by ranthal on 2008-08-15
> **dfreer said:**
> You'll want to check out what service is translating the server name to IP address and update it accordingly. It could be a DNS server, a WINS server, maybe a router that has something like this build in.

It's a DNS.

> **dfreer said:**
> If nothing else, you can edit your /etc/hosts file and add the server name with the update IP address. This means though if it ever changes IP again you will need to update /etc/hosts again too.

Yeah I did this a few days back when other problems with the server were coming up, was looking for a more elegant way to go about it.  I've changed it again but is there a good way to access the DNS?

> **dfreer said:**
> BTW, I'm pretty sure this wouldn't be a Ubuntu-only problem, unless there's something very unique about the way your Ubuntu machine is hooked up to your network.

You're correct about that I just typically run Ubuntu (though server uses Kubuntu) so thought I'd label it as such.

Thanks!

---

### Post by bab1 on 2008-08-15
The question that remains unanswered is; Why is your server's IP address changing?  You make it sound like it has happened more than once.  If it is assigned by DHCP, then you should reserve a permanent address by associating the MAC address of your servers NIC to a specific IP address in your DHCP server.  In any event server IP addresses should not be allowed to change under normal circumstances.

---

### Post by dfreer on 2008-08-15
Yes, a bit more information would be helpful. Is this a server you have access to at work (e.g. admin)? Are you having problems accessing it at work on the LAN or from home/internet? Do you have access to the DNS server that is translating the names to IP's (e.g. a local DNS server)? I'm just not quite sure what we're dealing with here.

---

### Post by ranthal on 2008-08-15
> **dfreer said:**
> Yes, a bit more information would be helpful. Is this a server you have access to at work (e.g. admin)? Are you having problems accessing it at work on the LAN or from home/internet? Do you have access to the DNS server that is translating the names to IP's (e.g. a local DNS server)? I'm just not quite sure what we're dealing with here.

Ah, ok.  It is a server at work that is set up in our lab.  It is on both the lab's LAN and the company network.  The DNS server is on the company network which I do not have access to.  The problem we have had has been with this server which is why the IP has changed since it's really only used by our dev group which is around 10 ppl.

The problem seems to be fixed since I edited my /etc/hosts file to associate the server name with the 172 ip address network and when I blew that away it was still ok (though the comp prob still remembers that association).  Either way I think the main problem is with the company's DNS server so I'm pretty much good to go, still just trying to learn more about Ubuntu, networking etc so thought I'd post and see what replies I got to hopefully get some insight.  Thanks guys ):P

---

