---
title: "VPN via Network Manager installs VPN DNS and removes ISP DNS"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by philws on 2008-01-28
I’m using Ubuntu 7.10 with Network Manager and OpenVPN (and am an Ubuntu virgin). The basic setup is fairly straight forward (given an import file and the required certificate and key files). What I can’t figure out how to do is to get DNS configured appropriately. Let me explain…

When not VPNed to work I can access internet sites fine. When I do VPN into work I can access my company’s internal network but cannot access the internet. What seems to happen is that the resolv.conf file is automagically updated when the VPN is started and reset on disconnect.

When disconnected it has my ISP’s DNS server listed. When connected it has my company’s DNS server. The company one doesn't seem to contain information for external sites, just company hosts.

How can I influence the content of resolv.conf to keep my ISP’s DNS server as the primary entry and my company’s DNS server as a secondary entry?

There is an update-resolv-conf in /etc/openvpn (the directory I put the certificate and key files) which has a comment about setting it as the up and down file in the *.conf file for the VPN connection. However, the Network Manager doesn’t provide any inputs for up and down scripts. How do I configure it? Or is there some other way of doing this (I'd like to use the Network Manager as it has a nice way of starting and stopping the VPN via the GUI)?

(I've seen [another thread]("http://ubuntuforums.org/showthread.php?t=665774") that seems related, but the "solution" seems too hacky and not resillient to updates to my company's network.)

Any and all help appreciated!

---

### Post by jakev383 on 2008-01-31
I have the same problem, and would love to find an even somewhat-easy solution.

---

### Post by schwieb on 2008-02-13
This issue seems to be a 'feature' of Network Manager, not Ubuntu.  I am yet to find a fix for it anywhere.  There is a workaround though.  Just run openvpn from the command line and feed it your .conf file like this:

sudo openvpn myserver.conf

Hope that helps.

---

### Post by mathiraj on 2008-02-13
i'm too having the same situation. let me know if anyone finds a solution for this...

---

### Post by clandestiny on 2008-03-30
> **philws said:**
> When not VPNed to work I can access internet sites fine. When I do VPN into work I can access my company’s internal network but cannot access the internet. What seems to happen is that the resolv.conf file is automagically updated when the VPN is started and reset on disconnect.

When disconnected it has my ISP’s DNS server listed. When connected it has my company’s DNS server. The company one doesn't seem to contain information for external sites, just company hosts.

This happens because your company's vpn server is configured to push DNS information to the clients.

> **philws said:**
> How can I influence the content of resolv.conf to keep my ISP’s DNS server as the primary entry and my company’s DNS server as a secondary entry?

Unfortunately, primary/secondary DNS doesn't work like that.  Secondary is only consulted if *connection* to primary cannot be made.  If you make your ISP's DNS primary and try to resolve an internal company name, you'll connect and receive a NOT FOUND response -- not really too helpful.

Your only other alternative that I can see would be to somehow get your vpn client to ignore the pushed DNS information (or somehow restore the default state of resolv.conf after connecting), and maintain entries for key names/addresses of your company's internal machines in /etc/hosts, so that both they and Internet addresses can be resolved.  (I know, it's a pain, but I don't see another way, if your company's DNS won't forward Internet DNS requests.)

---

### Post by stream303 on 2008-03-31
> **philws said:**
> How can I influence the content of resolv.conf to keep my ISP’s DNS server as the primary entry and my company’s DNS server as a secondary entry?

Are you behind a router that you have access to?

If so, put your dns primary and secondary addresses in the router's own setup page.  Works for me every time.

---

### Post by chilinski on 2008-03-31
Two things. Let's fix the DNS stuff first.

/etc/resolv.conf gets rewritten with EVERY dhcp connection. If you use dhcp, you can't plunk your DNS in resolv.conf. What you do is add a line to /etc/dhcp3/dhclient.conf. The prepend command works (there's another one but I don't remember it). So you add:

prepend nameservers x.x.x.x, y.y.y.y, z.z.z.z;

These nameservers will then always be used and will always appear in resolv.conf.

Your network people could also be blocking you from browing the internet when you have a vpn connection. There's a term for this, but I can't remember what it is. My Cisco PIX at work is configured this way. When they have a VPN connection, they can ONLY use resources on my network.

The thought here is that if someone compromises their machine through the internet they would have a direct, secure, encrypted vpn line into the guts of the network. Since we frown upon that, we shut off their ability to go anywhere else.

---

### Post by philws on 2008-04-23
> **stream303 said:**
> Are you behind a router that you have access to?

If so, put your dns primary and secondary addresses in the router's own setup page.  Works for me every time.

I am and have but...

> **clandestiny said:**
> Unfortunately, primary/secondary DNS doesn't work like that.  Secondary is only consulted if *connection* to primary cannot be made.  If you make your ISP's DNS primary and try to resolve an internal company name, you'll connect and receive a NOT FOUND response -- not really too helpful.

Bummer :(

> **clandestiny said:**
> Your only other alternative that I can see would be to somehow get your vpn client to ignore the pushed DNS information (or somehow restore the default state of resolv.conf after connecting), and maintain entries for key names/addresses of your company's internal machines in /etc/hosts...

Hmmm. Not great. I'll have to see if I can get work to make internet DNS available within VPN (not withstanding comments about security!).

Many thanks for you insight.

Phil :(

---

### Post by timcredible on 2008-04-23
what you're trying to do is called split tunneling.  see if there's an option for it in openvpn.  messing with dns won't help.

---

### Post by philws on 2008-04-23
> **chilinski said:**
> Your network people could also be blocking you from browing the internet when you have a vpn connection.

You could be right, though they don't block us when on the company network anyway...

Thanks.

---

### Post by philws on 2008-04-23
> **timcredible said:**
> what you're trying to do is called split tunneling.  see if there's an option for it in openvpn.  messing with dns won't help.

Thanks. I'll have a dig around and see what I turn up (though I suspect the Network Manager won't give me access to this anyway and I'd have to use openvpn from the CLI which isn't ideal).

---

### Post by jakev383 on 2008-04-23
Where are the openvpn config files for each VPN connection located on the client machine? I'm going to try putting my Windows version in Ubuntu. The Windows version allows me to still surf the 'net when connected to the VPN, but the Ubuntu one does not.
Thanks.

---

