---
title: "Name resolution in a home network with D-Link DI-624"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by sradhakrishna on 2008-05-10
Hi,

I have a home network set up through a wireless router D-Link DI-624, which has 4 ethernet ports as well. The router is connected to a ADSL broadband modem, through which I connect to the internet.

DI-624 has an entry in its web-based administration console, called Local Domain Name. Have given it a value MY-WLAN. Also enabled the option called DNS relay. Also, enabled DHCP server on the router. 

Have three PCs connected to my network, all of them running Ubuntu. These PCs have names - mypc1, mypc2 and mypc3. Am able to ping each one of them from another, using their IP addresses. Am able to access internet as well.

However, when I try to ping, say mpc2 from mypc1, using 'ping mypc2', it fails. The name mypc2 couldn't be resolved. 

My questions:

1.  What does the Local Domain Name on the DI-624 mean?? Does it implicitly mean that there is a DNS with the router?? If so, how do I attach my PCs to that domain??
2.  If DI-624 does not have a DNS, how could I set up DNS in my home network??

Any help regarding this will be greatly appreciated.

Thanks,
Radha.

---

### Post by MaindotC on 2008-05-10
[This link]("http://support.dlink.com/emulators/di624_revc/help_home.html") explains your first question.  My interpretation is that the "Local Domain Name" option is to name the device if it were to be part of a domain.  That would enable NetBIOS communication.

Replying to your 2nd question, you need a DNS server in order to resolve names.  Also, if your network and DNS settings are attained via DHCP, chances are the home router is using the DNS settings given by the ISP.  The router forwards your DNS requests to the ISP's DNS servers which don't know mypc1, 2, or 3.

You can set up a DNS server very easily however I only know how to configure it in Fedora 8 which uses the service called named (name daemon).  Ubuntu uses bind9 and the configuration files are confusing to me - probably because I'm used to Fedora.

Once you set up the DNS server, just tell each of your clients to use that address to resolve names, and then the router for DNS queries outside of your network in the /etc/resolv.conf.

I've a feeling I'll be getting more questions from you...

---

### Post by sradhakrishna on 2008-05-11
Thanks for the reply strAlan! That was quite helpful.

A little more about my set up. The ADSL broadband modem gets an IP from the ISP via DHCP. DI-624, the wireless router serves up a sort of intranet (LAN) within the devices that connect to it. All my PCs get an IP like 192.168.x.x, from a DHCP server that is running inside the wireless router. The wireless router was setup to point to the ISP's DNS, so I guess thats how name-to-address resolution happens for the internet.

Rightly guessed, I do have a few more questions. :-)

After your reply, I searched for Bind9 and skimmed through a few links that came up. Looks like thats the way to go about. However, all the articles talked about PCs that have static IP addresses and how they should be configured in Bind9's config files. 

I would like to get Bind9 working with dynamic addresses - my PCs get their addresses through DHCP on the wireless router. Any pointers in this matter will be of great help!

In the MS Windows world, the network settings give a way to add a PC to a domain. The user will have to mention the name of the domain and credentials powerful enough to add it to the domain. I guess there's a server running a DNS, and clients registering themselves by attaching themselves to the domain.

In Bind9, am assuming its somewhat similar. We have a server that's running Bind9. But what is the infrastructure on the client's front which will allow the client to 'register' themselves/ 'attach' themselves to the domain??

Is there some UI based application that the clients could run to attach the client to the domain?? That would make life a lot simpler for noobs like me!

Any help, again, will be greatly appreciated.

Regards,
Radha.

---

### Post by MaindotC on 2008-05-11
I don't really have the time to learn Bind9 because I have final exams this week but if you have any interest in using a Fedora box I can send you the configuration files and tell you how to configure them to your needs. I'm sure all you have to do is read the Bind9 documentation but at this time I don't have time for it.

If you'll entertain the idea of doing it in Fedora I can send you the stuff - don't need to worry about Windows domains or anything like that.  You just need to install the package called named and there are three files you edit - it's really easy.  Let me know!

---

### Post by mbarak on 2008-05-11
> **sradhakrishna said:**
> Thanks for the reply strAlan! That was quite helpful.

I would like to get Bind9 working with dynamic addresses - my PCs get their addresses through DHCP on the wireless router. Any pointers in this matter will be of great help!

In the MS Windows world, the network settings give a way to add a PC to a domain. The user will have to mention the name of the domain and credentials powerful enough to add it to the domain. I guess there's a server running a DNS, and clients registering themselves by attaching themselves to the domain.

In Bind9, am assuming its somewhat similar. We have a server that's running Bind9. But what is the infrastructure on the client's front which will allow the client to 'register' themselves/ 'attach' themselves to the domain??

Is there some UI based application that the clients could run to attach the client to the domain?? That would make life a lot simpler for noobs like me!

Any help, again, will be greatly appreciated.

Regards,
Radha.

First you are confusing the domains of the internet with Microsoft domains where you login.
A dns server has a list of names and ip-address
when your computers enter a name (ex: google.com in firefox for example) it asks the dns server what ip-address belongs to that name
the other computers don't really "join" a domain, they become a part of it simply by being referred by the dns server.

you will probably want to host your own dns server (bind9 in ubuntu) and create your own domain (for example, on my network i created the "home" domain with records for "server.home", "laptop.home" etc..) and your computers can talk to each other with mypc1.domain

you would simply have to edit the files /etc/resolv.conf on each computer to read something like this:
```

nameserver ip.of.dns.server
search name_of_domain

```the "search" allows you to type mypc1 instead of mypc1.domain

to get this to work with dynamic ip-address you would want to host your own dhcp-server (dhcp3-server) and configure dynamic-dns.  that way when your server computer gives ip-addresses to your other computers, it will also update the dns server so all your computers can talk to each other, without them having static ip-addresses
***your dns server (which, i'm assuming will also be your dhcp-server) must have a static ip address.
to configure dynamic-dns: first create your domain (there are many guides online) then google a guide for dynamic-dns (there are a few out there that will help you out)

after you have it all set up, you will have to turn off dhcp on your router

EDIT: o, and for a graphical solution you can install webmin (download the .deb from their website) or install gbindadmin and gdhcpd.  i suggest editing the configuration files by hand as you learn more that way and, once you're finished you will understand how it all works - which is always a perk :)
if editing configuration files isn't your thing, i can vouch for webmin - it works very well

---

### Post by MaindotC on 2008-05-11
I used GadminTools for BIND and it was pretty sweet.  Have you configured Bind9 before?

---

### Post by mbarak on 2008-05-12
yes i have - do you need help with something?

---

### Post by MaindotC on 2008-05-12
If I could have a shortcut guide for configuring it I'd appreciate it.  I just don't have time to read the documentation.  It's up to you.

---

### Post by mbarak on 2008-05-13
install the dns server and dhcp server with this command:
```
sudo apt-get install bind9 dhcp3-server
```
in the file /etc/bind/named.conf.options
change this line
```

forwarders {
         192.168.1.1;
     };

```
*change 192.168.1.1 to your isp's (or your routers) dns server (or servers)

in the file /etc/bind/named.conf.local
you have to declare your zones - both the forward zone and reverse zone
```

zone "example.com" {
    file "/etc/bind/zones/example.com/forward";
    type master;
};

zone "1.168.192.in-addr.arpa" {
    file "/etc/bind/zones/example.com/reverse";
    type master;
};

```
you can put the zone files anywhere readable by the bind user/group (i.e. - under the /etc/bind/ folder would be alright)

then you make your zone files like this:
forward zone
```

$TTL    86400
@    IN    SOA    name.of.nameserver. email.address.hotmail.com (
              2008050900        ; Serial (can be anything (use date+serial) increment when you change the file
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
              86400 )    ; Negative Cache TTL
;
@    IN    NS        name.of.nameserver
@        MX    10    name.of.mailserver
name.of.nameserver       A    192.168.1.1
comp2                            A    192.168.1.2
alternativename              CNAME comp2
outside                           CNAME finish.outside.domains.with. ;finish outside domains with a period

```

reverse zone:
```

1.168.192.in-addr.arpa    IN SOA    name.server. email.address. (
                2008050900 ; serial
                604800     ; refresh (1 week)
                86400      ; retry (1 day)
                2419200    ; expire (4 weeks)
                86400      ; minimum (1 day)
                )
            NS    nameserver.example.com. ; don't forget the dot at the end
1            PTR    nameserer.example.com.
2            PTR    comp2.example.com

```
and, unless i did something really wrong, that should work.
just change the /etc/resolv.conf to say:
```

search example.com
nameserver ip.of.dns.server

```

test it with nslookup (enter a bunch of domains (ex: google.com) and your local domains (ex: comp2)

or, try
dig comp2.example.com
and dig -x ip.address

---

### Post by MaindotC on 2008-05-14
Hey, mbarak - thanks for posting these instructions.  I don't think I'll be able to test it anytime soon but I'll bookmark this.

---

### Post by mbarak on 2008-05-14
just to let you know - getting this to work is only 1/3 of the work
if you want dynamic dns to work you have to properly set up dhcp, and then properly integrate the two

---

### Post by MaindotC on 2008-05-14
I work on a campus environment that has the whole 136.204.x.x network so each of us get public addresses no matter where we plug in.  However, I don't own any domains, so I usually host a DNS server for a lab project and don't allow dynamic DNS as I usually use a fake domain and don't want to screw w/ the other records on the internet.  I usually just have testing clients to point their name resolution to my DNS server and then they can check out my stuff.  But thanks!

---

### Post by singamayya on 2008-10-19
Hello,

I use the same wireless router at home and was trying to do the same thing the original poster was.

Here's my solution:

1. Enable the "DNS Relay" option in the Router's "LAN" section (found at: [http://192.168.0.1/h_lan.html](http://192.168.0.1/h_lan.html))

2. Add the following line to your /etc/resolv.conf file:

```
search localdomain
```

My entire /etc/resolv.conf file looks like this:

```

nameserver 192.168.0.1
search localdomain

```

This was much easier than installing bind9, etc. because the router acts as our name server instead.

Hope this helps, cheers!

---

