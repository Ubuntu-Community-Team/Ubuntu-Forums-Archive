---
title: "DNS quit working after Windows network update"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by sampsonats on 2015-02-04
I have several Ubuntu 14.04 LTS servers that exist in a Windows centric network. Late last year, there was a Windows network update that broke the DNS functionality in all my Ubuntu servers. Our IT department is Windows only and doesn't care too much about Ubuntu issues.  I'm pretty much on my own to fit in and live in this Windows network.

My question is, what does Ubuntu expect from a network for DNS to work? For example, does Ubuntu expect "Allow Dynamic Updates" to be enabled on a Windows DNS server? Does Ubuntu expect the DHCP server to register its hostname with the DNS server automatically?

Some high level help would be appreciated and allow me to ask better questions to our Windows IT guy.

Thanks!
Todd

---

### Post by SeijiSensei on 2015-02-04
Are you trying to resolve hostnames to their IP addresses or their reverse?  Hostnames within your local network, or public Internet hostnames?

Here are some tests you can try.  First, let's assume the Windows DNS server is at 10.10.10.10.  Try resolving an internal hostname on the Windows network with
```
host hostname 10.10.10.10
```
to force use of that DNS server.  Suppose "hostname" resolves to 10.10.10.100.  Now try:
```
host -t ptr 100.10.10.10.in-addr.arpa
```
Does that return "hostname"?  If so, you've got proper forward and reverse resolution within the Windows network.

Now try the same thing with, e.g., "www.google.com".  What happens?

Are you getting the DNS servers via DHCP, or are they specified in /etc/network/interfaces?

---

### Post by sampsonats on 2015-02-04
I think my Ubuntu hosts are getting the DNS address from DHCP. It's not [COLOR=#000000]specified in /etc/network/interfaces.[/COLOR]
I'm trying to resolve hostnames to IP addresses only on our LAN.  In fact, ping [www.google.com]("http://www.google.com") works just fine.

> dfr@desktop:~$ ping [www.google.com]("http://www.google.com")
PING [www.google.com]("http://www.google.com") (74.125.201.104) 56(84) bytes of data.
64 bytes from 74.125.201.104: icmp_seq=1 ttl=45 time=259 ms
64 bytes from 74.125.201.104: icmp_seq=2 ttl=45 time=73.0 ms

Ping station3 host on LAN does not work
> dfr@desktop:~$ ping station3
ping: unknown host station3

Ping station3 by ip address works
> dfr@desktop:~$ ping 195.1.1.152  <---------------------ip address of station3
PING 195.1.1.152 (195.1.1.152) 56(84) bytes of data.
64 bytes from 195.1.1.152: icmp_seq=1 ttl=64 time=0.956 ms
64 bytes from 195.1.1.152: icmp_seq=2 ttl=64 time=0.799 ms


> dfr@desktop:~$ host station3 195.1.1.103
Using domain server:
Name: 195.1.1.103
Address: 195.1.1.103#53
Aliases: 


Host station3 not found: 2(SERVFAIL)


> dfr@desktop:~$ host -t ptr 152.1.1.195.in-addr.arpa
152.1.1.195.in-addr.arpa domain name pointer c830dn.maginst.local.



I think the DNS server has no record of any of my Ubuntu host names.

---

### Post by SeijiSensei on 2015-02-04
What if you use the fully-qualified domain name for station3 within the local network, e.g., station3.example.com?  If that works, your machine isn't getting the dns-search parameter from DHCP.  That provides the domain portion that should be appended to "unqualified" hostnames like "station3".

If you're using Ubuntu in a Windows Active Directory environment, you should look into using [Power Broker](http://askubuntu.com/questions/452904/likewise-open-14-04-other-easy-way-to-connect-ad), formerly known as "likewise-open".

---

### Post by sampsonats on 2015-02-04
Using FQDN doesn't help.
> dfr@desktop:~$ ping station3.maginst.local
ping: unknown host station3.maginst.local

Our network does use Windows Active Directory. Everything used to work until early December last year. I took a quick look at Power Broker.  It looks somewhat complex.  I would rather not have to deal with it.

Is it the case now that Ubuntu cannot coexist, (with DNS anyway), with Windows machines on a Windows network without installing Power Broker?

---

### Post by sampsonats on 2015-02-04
I got it working.  I found this with Google:
> If you really want your Linux into your DNS namespace you'll have to :
1 - On your DHCP server (if it's a Windows) : 
Go on scope properties / DNS / enable : Dynamically update DNS A and PTR records for DHCP clients that do not request update
2 - On your DNS : Right click on your zone / Properties / General / set Dynamic update to : Nonsecure and Secure

#2 was already set as above. Changing #1 to as above fixed the problem.

We have to deploy to various customers networks. If they all don't have the settings as above, I'll run into problems.  Would the Power Broker solution make us more tolerant of our customer's network settings?

Thanks for all the help!

---

