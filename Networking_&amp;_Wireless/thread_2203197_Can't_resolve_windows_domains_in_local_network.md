---
title: "Can't resolve windows domains in local network"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by Rafal_Baba on 2014-02-02
I've installed ubuntu on my computer at work because I think it is a perfect system for a web developer but I got some issues. I can't resolve domains from windows DNS server. Basically, we have two servers, one is Windows server (DNS sever) and another one is ubuntu 12.04 (LAMP). So every time when I create new project I have to create new alias on DNS server for example *project1.localdomain.local* which points to ubuntu server. On ubuntu server I have to create the project in directory /var/www/project1/htdocs. Everything works for computers in local network with windows or for macs. So basically when I am trying open a link [http://project1.localdomain.local](http://project1.localdomain.local) in a browser it works. But when I do it on my computer with fresh ubuntu installation it doesn't. It looks like ubuntu can't resolve local domain where DNS server is.


So my network looks like that:
10.10.16.1 - DNS server - windows server
domain - test


I've already tried resolved the problem adding lines to /etc/resolve.conf file
```
domain test
nameserver 10.10.16.2

```

/etc/NetworkManager/NetworkManager.conf file I commented out line 


```
#dns=dnsmasq

```

/etc/dhcp/dhclient.conf I added lines
```
supersede domain-name "test";
prepend domain-name-servers 10.10.16.1, 10.10.16.2;

```

But it doesn't work.


On windows or mac I don't have to do any additional configuration to make it work. Below is a network connection details from a computer with windows.
[ATTACH=CONFIG]250021[/ATTACH]

---

### Post by TheFu on 2014-02-02
Microsoft decided to use the term "domain" in a different way than the rest of the universe had been using it for 40 years, so often confusion happens.
Active Directory "domains" have NOTHING to do with DNS domains.
Further, Microsoft knew their customers well and made systems automatically discover each other using the SMB/NMB protocols. These may or may not run on TCP/IP. Linux machines do not normally pay any attention to either SMB or NMB.

With 12.04, modifying /etc/resolv.conf doesn't help since it is overwritten every boot by the resolvconf process. Settings must be put inside the /etc/network/interface file instead.  Using  "/etc/resolve.conf" is worthless - incorrect spelling.  Computers do what we tell them, not what we mean to tell them.

I don't use DHCP here for servers, think using it for any server is ... less than optimal.

With just a few computers on the network, I find having all of them in the local /etc/hosts file work easiest for me. Did you put that project1.localdomain.local  hostname into the Linux computer /etc/hosts files?

I haven't any clue about OSX.  Tried it for a few weeks and found it extremely frustrating.

---

### Post by Rafal_Baba on 2014-02-02
Hi TheFu, thank you for your answer, I haven't tried put the domain to /etc/network/interface there is only /etc/network/interfaces file, the same with the /etc/hosts file I haven't put the [COLOR=#000000]project1.localdomain.local hostname[/COLOR] . I am gonna do it tomorrow at work. But anyway it is strange that everything works on computers with windows connected to the local network which resolve the local domain in this cases "test" which points Windwos DNS sever (10.10.16.2) I don't understand why Ubuntu need additional configuration. I didn't create the configuration with DNS server on windows and LAMP on separate machine but anyway it works for computers with ios and windows. Sorry I am not a networking expert and sorry if I confuse basic terms ;)

Thank you for you help, let you know if it works

---

### Post by TheFu on 2014-02-03
It may be strange to you, but Microsoft has a habit of "embrace and extend" ... those extensions are locked up in patents. Nice. So when other computers don't work the same, it isn't the failure of the other operating system.  DNS is fairly standard, so if your Linux machines are on the same "domain" and are setup to use the default search correctly AND the DNS server is setup to answer for both local and FQDN queries, then it will work.

The "interfaces" file DNS settings are per-NIC and look like :
```
  dns-nameservers 10.10.16.2
  dns-search localdomain.local
```
Does this make sense?  Those settings go inside the same stanza with address 192.168.0.xx.

Name resolution via DNS is something that UNIX invented and that the rest of the world follows ... "WINS" name resolution is something that Microsoft added and I couldn't guess at the reason. It wouldn't be nice.

---

### Post by Rafal_Baba on 2014-02-04
Hi TheFu, I put the project1.localdomain.local hostname into /etc/hosts file and it works of course, but problem is that I will have to do it for each project which I gonna create what actually is not a big problem but it would be better for me if it work automatically (On the same machine I have Microsoft Exchange Server). I still use DHCP so I don't know if I can put 

dns-nameservers 10.10.16.2
dns-search localdomain.local

to the file, can I?

---

### Post by TheFu on 2014-02-04
There is no automatic DNS registration when a new IP/hostname is added to the network for many important reasons. DNS must be manually configured for every IP-to-name lookup.  That is the way that IP was designed.

I don't understand what MS-Exchange has to do with anything and I don't understand which file on which system the dns-na.... settings would be used.  Also, I don't understand what DHCP has to do with this - servers need to have static IPs, period.

---

### Post by Rafal_Baba on 2014-02-05
Thanks a lot TheFu, my problem has been resolved on another forum, actually it was very simple. Below is what I had to do.
[SIZE=2][FONT=arial][COLOR=#333333]I had to change hosts line in /etc/nsswitch.conf file
[/COLOR]
[/FONT][/SIZE]```
[SIZE=2][FONT=arial]hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4[/FONT][/SIZE]
```[SIZE=2][FONT=arial]
[COLOR=#333333].local is used by mDNS (Avahi), dns should comes first.[/COLOR]
[COLOR=#333333]More information here [http://www.lowlevelmanager.com/2011/09/fix-linux-dns-issues-with-local.html](http://www.lowlevelmanager.com/2011/09/fix-linux-dns-issues-with-local.html) 

thanks for user Sneetsher from askubuntu.com forum, he saved me a lot of time.[/COLOR][/FONT][/SIZE]

---

### Post by TheFu on 2014-02-05
Thank you very much for posting the solution

---

### Post by bab1 on 2014-02-05
> **TheFu said:**
> It may be strange to you, but Microsoft has a habit of "embrace and extend" ... those extensions are locked up in patents. Nice. So when other computers don't work the same, it isn't the failure of the other operating system.  DNS is fairly standard, so if your Linux machines are on the same "domain" and are setup to use the default search correctly AND the DNS server is setup to answer for both local and FQDN queries, then it will work.

The "interfaces" file DNS settings are per-NIC and look like :
```
  dns-nameservers 10.10.16.2
  dns-search localdomain.local
```
Does this make sense?  Those settings go inside the same stanza with address 192.168.0.xx.

Name resolution via DNS is something that UNIX invented and that the rest of the world follows ... "WINS" name resolution is something that Microsoft added and I couldn't guess at the reason. It wouldn't be nice.

A couple of points here since you asked... ;-)

WINS is nothing more or less than the NETBIOS naming database.  It is only needed on networks with more than one subnet.  It has nothing to do with the question of DNS resolution.  DNS and WINS are about the same age.  Both are mid 1980's technology.  It is worth noting that Windows machines do not need DNS to be identified by name, but that name may be the COMPUTER NAME (NETBIOS).  I think it is important to also note that MS Active directory is nothing more than LDAP, DNS and KERBROS.  MS domains are DNS domains.  There is nothing special in that regard.  Are there MS extentions? Active Directory DNS is updated automatically. The host should be introduced to the AD LDAP server for this to work correctly.  As you know, for the longest time Unix style DNS servers were only manually updated.

The OP's post's are confusing at best.  I think the problem is AVAHI.

Edit: Ah ha!  Ninja'd by the OP.    I missed his posts when went to dinner in the middle of this post.  LOL

---

### Post by bab1 on 2014-02-05
> **TheFu said:**
> There is no automatic DNS registration when a new IP/hostname is added to the network for many important reasons. DNS must be manually configured for every IP-to-name lookup.  That is the way that IP was designed.

I don't understand what MS-Exchange has to do with anything and I don't understand which file on which system the dns-na.... settings would be used.  Also, I don't understand what DHCP has to do with this - servers need to have static IPs, period.

I believe BIND9 allows for automatic DNS updates now.

---

