---
title: "DNS and home network questions"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by yellowband on 2007-08-13
hello. i'm trying set up a more solid home network and i have run into a few questions.  

1. I want to use dnsmasq to set a little DNS server to reslove my local host names.  A lot of guides say to enter my "domain" name. What exactly is my domain name?  i have never purchased a domain.  Can i use any name i like?  Is 'HOME' my domain name, so long as i specify that on all of my hosts?

2. The documentation says that dnsmasq works behind a NAT (firewalled computer). How do i set this up per se?  or is it assumed that a NAT is present when you are using a linksys router and cable modem?

3.  I don't think i want to us DHCP as i dont see the benefits of it and it is one more hassle to set up.  is there any reason why i should be using DHCP?  static ip addrsses are more appealing to me.  

4. Finally, i was fiddling with my router settings ( a linksys wrt54g) and in its settings there is a "HOST" field and a "DOMAIN" field. I set the HOST filed to something like dars_router, and the DOMAIN filed to HOME.  After a restarrt of my computers my whole network was buggered.  I could not ping any addresses (got an error saying the ip address could not be reached).  What happened here?  should one not give their router a host/domain name? or did i get teh domain thing wrong?

Sorry for the noobish questions but DNS?DHCP confuses the helll out of me.  Thanks for any help at all.

---

### Post by yellowband on 2007-08-13
any answers?

---

### Post by bluenova on 2007-08-13
The easiest way to handle domain names on a small network is to edit /etc/hosts on one machine, adding all the ip's and names, then just copy that file to all the other machines.

No reason to use DHCP if you don't have more than a few dozen machines, or laptops that connect to other networks.

RE your router, I would reset it and start a fresh, as I said there is no need for DHCP or domain servers, for any network with less than a few dozen of computers, it's just more work than it's worth.

---

### Post by raijinsetsu on 2007-08-13
Answers, in order:
1) "HOME" is a perfectly fine domain name. The only consideration when choosing an internal domain name is that it does not shadow another external network.

2) If you have a router, you have a NAT (unless you disabled it). If you didn't have a NAT, depending on your ISP, you could have some or no connectivity.

3) DHCP... your router will have this enabled by default, as will all Windows (and most Linux) clients. It allows network clients to be added and removed without manually configuring each one. Unless you have need for a specific network configuration, I would choose DHCP

4) When you changed the HOST setting on your router, it is most likely (from your description of the problem) that the router tables did not get updated within the router. This means, for example, that "192.168.2.1" still points to "ComputerA.OldDNS", when it should point to "ComputerA.NewDNS". If you do a hard reset of the router, the tables should be wiped and the new pointers SHOULD be setup. I suggest backing up your router settings (there's a tool on the router's configuration page), just in case.

---

### Post by yellowband on 2007-08-13
thanks for the help!

If i choose to simply edit the /etc/hosts file on each computer ( a good idea by the way) will a windows computer able to see the hostnames on the network?  

Is it advisable to give my router the same domain name as the hosts on my network?  it was working before by leaving it blank (the field for my routers DOMAIN that is).

---

### Post by Synflux on 2007-08-14
Windows also has a 'hosts' file. It is located in %windir%\system32\drivers\etc and can be edited in much the same way.

The router's domain setting is different, some ISPs use it but you can leave it blank unless they tell you otherwise, it won't affect your internal network in any way.

:)

---

### Post by yellowband on 2007-08-14
thanks synflux

ya i wished i would've read the option description before i messed with the router domain name, it really bungled up my network.  

One other thing

i tried to get a little DNS server going on my main server using dnsmasq.  I have DHCP turned off on my router and on this server. Also i did not supply a domain name to any of my computers.  

I tried to to change the /etc/resolv.conf on my computer to point to my server that has dnsmasq on it (nameserver 192.168.1.100). On my server, which has dnsmasq, i kept my ISP provided DNS ip addresses.  However, this setup dgives me problems.  No computers can reach other computers on the network.  

My question is: why can my hosts not resolve DNS addresses when i point them to my DNS server's ip. AND more importantly, how CAN they resolve local hostnames when i use my ISP's supplied DNS servers.  these servers are external to my network so how can computers within my network resolve each other using them? that boggles my mind.

---

### Post by Synflux on 2007-08-14
Hello,

I'm sorry but I've never tried installing a DNS server on Linux so I can't really help you there. I would guess that you need to configure it to have 'forwarders' so it can pass on un-resolved queries to other dns servers (the ones your ISP supplied), something to do with recursive queries.

Perhaps someone who has dnsmasq running might be able to take over and help you more.

Note that windows will use Netbios to resolve names before it attempts to use dns, there's also an option somewhere where you configure the order in Linux but I can't remember where it is off the top of my head! Sorry.

Best of luck with it. :)

---

### Post by yellowband on 2007-08-14
ya i think you are talking about /etc/nsswitch.

i'll poke around the dnsmasq documentation for more info.

Can anybody answer my other question though?  how can my ISP DNS server resolve my local hostnames ?  I even found that when i was using openDNS it could resolve the hostnames, although it took forever.  

I thought that my whole network appeared tot eh interwebs as one ip address, then my router routed traffic to each local host in my network.

---

