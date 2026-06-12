---
title: "samba dns server"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by debianbryan on 2008-02-04
i tried searching around the forums and i think somebody may have already answered my question but i'm not quite sure.  i've tried to rtfm, and i thought i had done everything correctly but it's still not working:

i have two subnets, 192.168.1.x and 192.168.2.x, each with an ubuntu server with samba functioning as a pdc serving several windows boxes on either end.  this setup works just fine, however since the windows workstations are on separate subnets they do not resolve local names on the other network.  there are only a handful hostnames that i would like to resolve, so dynamic name resolution is not necessary and maintaining the names in the hosts file would be ideal.

i'm under the impression that i want to configure samba as a dns and/or wins server, and i believe that i have done this correctly.  i've configured one of the windows boxes to point to the samba server.  pinging one of the hostnames from ubuntu resolves correctly because there is an entry in the hosts file, but pinging the same hostname from the windows box that is using the samba server as dns and wins gives me goose eggs.  am i making the correct assumptions or am i way off?

---

### Post by HermanAB on 2008-02-04
Well, since the subnets are so small, can't you just make them a single subnet and avoid the whole head-ache?

---

### Post by joebeasley on 2008-02-04
Setup one of your samba servers as a WINS server.  Change "wins support = no" to "wins support = yes" on one of the samba boxes.  Then point all other machines to that one for wins.

---

### Post by debianbryan on 2008-02-04
thanks for the replies guys

the workstations are not in the same physical location and are connected via T1 that failover to cable, so they are configured as two subnets that route to one another via a routing network, not something that i can change.

i've set wins server = yes already, but no difference.  ipconfig from the windows workstations confirms that it is using the ubuntu box for wins, but i still can't ping via hostname.  am i correct that if i can ping the hostname from ubuntu and it is set up as a wins server i should be able to ping the same name from a windows workstation that's pointing to it for wins?

---

### Post by patryk77 on 2008-02-05
You cant' access a private network address over the internet.

So if you're at location A sitting on computer 192.168.1.4 and you ping 192.168.2.4 at location B, it will not work.

If you want to use DNS for name resolution you need the BIND package
[http://www.isc.org/index.pl?/sw/bind/index.php](http://www.isc.org/index.pl?/sw/bind/index.php)

I'm not too sure of what you are trying to achieve, but it sounds more like a VPN that you would need.

[http://computer.howstuffworks.com/vpn.htm](http://computer.howstuffworks.com/vpn.htm)

---

### Post by debianbryan on 2008-02-05
> **patryk77 said:**
> You cant' access a private network address over the internet.

So if you're at location A sitting on computer 192.168.1.4 and you ping 192.168.2.4 at location B, it will not work.



sorry for not being clear: we are using a T1 routed vlan to connect our subnets so that the two subnets can access each other internally.  however, since name resolution does not occur on this level it is the only thing that i am having trouble with.  so i can ping workstations at location B from location A using their internal addresses.  i can ping location B's workstation netbios names from location A's ubuntu box because the entries are in its host file, but i cannot ping the same names from location A's workstations that are using the ubuntu box as a wins server.

---

### Post by debianbryan on 2008-02-07
i've got it figured out, i just wanted to share my solution here because when i google my issue this thread actually pops up pretty high in the result list.

windows xp has a tendency by default to perform name resolution by wins if the name is not qualified.  instead of using a wins server i ended up going with dnsmasq and serving the domain suffix to all of my windows workstations so.  this way when i attempt to resolve **hostname** on the workstations the domain is appended and it automatically resolves **hostname.domain** through dns instead.

---

