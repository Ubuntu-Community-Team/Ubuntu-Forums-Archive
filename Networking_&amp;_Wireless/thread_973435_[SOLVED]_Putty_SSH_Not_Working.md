---
title: "[SOLVED] Putty SSH Not Working"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by arcticool on 2008-11-06
I have just installed VMWare Workstation and loaded an Ubuntu 7.10 image (link below if you're curious) which seems to work fine as far as browsing the web, but Putty SSH isn't working. It just times out and says 'unable to open connection to 192.168.42.201:'. I know the IP is good, and the Putty config is the same as that on Putty on the host XP machine which works fine. Putty was installed through Synaptic Package Manager and seemed to install OK. I've tried both network connection types on the VMWare (Bridged and NAT) and again both work fine for browsing the web but no dice on the Putty. 

Any suggestions for troubleshooting?

BTW, I got the Ubuntu image here:
[http://jars.de/linux/ubuntu-710-vmware-image-download-english](http://jars.de/linux/ubuntu-710-vmware-image-download-english)

Thanks in advance!

Jack

---

### Post by arcticool on 2008-11-07
Anyone?

---

### Post by jimv on 2008-11-07
Can you give me the output of 'ipconfig /all' from the XP machine, and 'ifconfig' from the Ubuntu vm?

---

### Post by arcticool on 2008-11-07
> **jimv said:**
> Can you give me the output of 'ipconfig /all' from the XP machine, and 'ifconfig' from the Ubuntu vm?

Sure, from the XP machine:
VMNet8:
        IP Address. . . . . . . . . . . . : 192.168.121.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
VMNet1:
        IP Address. . . . . . . . . . . . : 192.168.38.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
Local Area Connection:
        IP Address. . . . . . . . . . . . : 192.168.18.44
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.18.254
        DHCP Server . . . . . . . . . . . : 192.168.9.3
        DNS Servers . . . . . . . . . . . : 192.168.9.2
                                            192.168.9.3
        Primary WINS Server . . . . . . . : 192.168.19.19
        Secondary WINS Server . . . . . . : 192.168.9.24

From Ubuntu VMWare Guest:
inet addr: 192.168.18.121 Bcast:192.168.18.255 Mask: 255.255.255.0

Lo Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0

---

### Post by arcticool on 2008-11-10
Does this help?
Any ideas for troubleshooting this much appreciated.
Thanks again,

Jack

---

### Post by phillik747 on 2008-11-10
I would try manually installing Openssh just to be sure it was on the image.

```
apt-get install ssh openssh-server
```

Also I dont see any network of 192.168.42.0 on the print out of the xp machine. If you were to bridge the connection it would need to be on the 192.168.18.0 network. I'm confused, only had 1/2 a cup of coffee, but you put that putty is trying to connect to 192.168.42.201 but the VMWare Guest is on 192.168.18.121.  Did you point Putty to 192.168.18.121?

---

### Post by arcticool on 2008-11-10
> **phillik747 said:**
> I would try manually installing Openssh just to be sure it was on the image.

```
apt-get install ssh openssh-server
```

Also I dont see any network of 192.168.42.0 on the print out of the xp machine. If you were to bridge the connection it would need to be on the 192.168.18.0 network. I'm confused, only had 1/2 a cup of coffee, but you put that putty is trying to connect to 192.168.42.201 but the VMWare Guest is on 192.168.18.121.  Did you point Putty to 192.168.18.121?

Yep, that's right, I set Putty to connect to 192.168.42.201, same as I always have on the Guest machine. Now I'm no networking expert, in fact I don't know much in that regard, but I suspect that the 192.168... of the corp net is getting confused with the 192.168... on the virtual machine. Running Wireshark on the host machine when I connect with Putty from there I see my machine makes a TCP call directly to the server I'm connecting to, the server responds with TCP then the two exchange keys and its SSL from there...

When I do the same from the guest machine, Wireshark shows the guest machine instead of TCP first sending a DNS call 'Standard Query A 192.168.42.201companyname.com' which responds with 'Standard query response No such name'.

I'll give the openssh a shot next.

Side note: on VMware, apparently the virtual machine traffic cannot be seen from the host machine. When I run Wireshark from the host looking for traffic from the guest's IP I see nothing at all.

---

### Post by phillik747 on 2008-11-10
It looks to be that your computer your trying to connect from is on a completely different network than the Ubuntu box.  Without vmware to connect the to networks you would need a router (or layer 3 switch) to connect the 192.168.18.0/24 network to the 192.168.42.0/24 network. 

I would revisit the network settings in vmware and use a NAT or Bridge setup to allow the two networks to 'see' each other. Making sure that a bridge connection is allowing the DHCP server to give it an ip on the 192.168.18.0/24 network.  Or if you know the DHCP range you can give it a unused static ip to something outside of that range. ie: if the DHCP range is 192.168.18.100-192.168.18.150 use 192.168.18.1-192.168.18.99

If you use NAT then VMware will translate from network 192.168.42.0 to 192.168.18.0 _kind of like_ a router but the two pcs wont be able to see one another.

Also try a ping/traceroute to the remote pc(192.168.42.201).  Since DNS is looking for 192.168.42.201 it means that the pc is trying to resolve something it know nothing about so it sends the request out to the DNS or default gateway.  

I suspect that when you do tracert 192.168.42.201 on the xp machine your first hop will be 192.168.18.254 and then your DNS servers. Which means that the XP box has no idea of how to get to 192.168.42.201.  

Something else to try is to putty using the host name. Vmware should be able to translate that request. Im using vmware server so I'm not sure how this will work with vmware workstation.

*I assume that these are all classfull networks (255.255.255.0)*

Please clarify:

Are you running putty from the XP machine or the Ubuntu box? Meaning...are you trying to connect from XP to the Ubuntu box or vis versa....

---

### Post by arcticool on 2008-11-11
> **phillik747 said:**
> It looks to be that your computer your trying to connect from is on a completely different network than the Ubuntu box.  Without vmware to connect the to networks you would need a router (or layer 3 switch) to connect the 192.168.18.0/24 network to the 192.168.42.0/24 network. 

I would revisit the network settings in vmware and use a NAT or Bridge setup to allow the two networks to 'see' each other. Making sure that a bridge connection is allowing the DHCP server to give it an ip on the 192.168.18.0/24 network.  Or if you know the DHCP range you can give it a unused static ip to something outside of that range. ie: if the DHCP range is 192.168.18.100-192.168.18.150 use 192.168.18.1-192.168.18.99

If you use NAT then VMware will translate from network 192.168.42.0 to 192.168.18.0 _kind of like_ a router but the two pcs wont be able to see one another.

Also try a ping/traceroute to the remote pc(192.168.42.201).  Since DNS is looking for 192.168.42.201 it means that the pc is trying to resolve something it know nothing about so it sends the request out to the DNS or default gateway.  

I suspect that when you do tracert 192.168.42.201 on the xp machine your first hop will be 192.168.18.254 and then your DNS servers. Which means that the XP box has no idea of how to get to 192.168.42.201.  

Something else to try is to putty using the host name. Vmware should be able to translate that request. Im using vmware server so I'm not sure how this will work with vmware workstation.

*I assume that these are all classfull networks (255.255.255.0)*

Please clarify:

Are you running putty from the XP machine or the Ubuntu box? Meaning...are you trying to connect from XP to the Ubuntu box or vis versa....

Yep, you were correct. I needed the Ubuntu VM on the 192.168.18.xxx then everything worked fine. Took a little bit of tinkering- had to turn off NAT and use bridged connection and 'replicate physical network connection state' now its good to go.
Thanks!

Jack

---

### Post by Iowan on 2008-11-11
Mark this one [SOLVED] (under Thread Tools) and get on to more productive things  ;)

---

### Post by arcticool on 2008-11-12
> **Iowan said:**
> Mark this one [SOLVED] (under Thread Tools) and get on to more productive things  ;)

OK, done- thanks.

---

