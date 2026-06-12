---
title: "Access web pages hosted on Windows"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by vairoj on 2007-02-07
I have a Windows server that hosts some internal web applications. From Windows clients, we can access these web from any browser though the computer name. For example, if the Windows computer name is **tiger**, I can access the web through URLs such as **http://tiger:8080**. However, when using Ubuntu client, accessing through this URL does not work.

Are there any configuration required in order to allow Ubuntu clients access these web the same way as from Windows clients?

---

### Post by amohanty on 2007-02-08
I hope you are running the windows server on a separate machine :)

If so, no no special config is required. However, theres no way for the ubuntu machine to know that the windows box is called tiger. Try using the ip of the windows machine. The reason windows machines are able to do that is windows uses something else on top of the regular networking stuff.

Look at my post [here]("http://ubuntuforums.org/showpost.php?p=2107357&postcount=2"). You will need to add the hostname and ip it tiger and tiger's ip address to /etc/hosts for that to work.

HTH
AM

---

### Post by vairoj on 2007-02-08
This works if the IP of those machine are static. However, in my case they are all dynamic IP from a DHCP server.

Are there any other approaches?

---

### Post by amohanty on 2007-02-08
YOu could have a script do that. However even in a dhcp lan, if you notice, the ips dont change much because the dhcp leases are really long. So unless explicitely specified and enforced, the likelihood of the ips changing is low. 

Or you could run your dns server, or use static ips (internal ips) for the machines.

HTH
AM

---

### Post by tturrisi on 2007-02-08
Why on earth are you running a server on a comp that uses a dynamic ip address? (bad idea) 
Very simple to fix,
just rt click My Network Places > Properties,
rt click Local Area Connection > Properties,
select TCP/IP Internet Protocol in the list, click the Properties Button,
check the radio button "Use the following ip address",
and enter the router address as the Default gateway,
and enter the router address as the Preferred DNS server. 
Bingo, the windows serevr ip address never changes!

The rest of the client computers can use dynamic addresses.

---

### Post by koenn on 2007-02-08
The problem is indeed that your Ubuntu machines cant translate a ("NETBIOS") name such as 'Tiger' to an ip address. Using ip addresses in the url is a good troubleshooting trick / workaround, but not really an elegant sollution. 

Netbios was a Microsoft protocol for small networks - Linux traditionally uses DNS. 
the Ubuntu's should be able to use DNS to translate names to addresses. DNS uses socalled "fully qualified domain names" - like tiger.mynetwork.xx in stead of just 'tiger'. If you have a DNS server running (eg on the windows machine), that should do the trick. You can then also (probably) use 'tiger' by itself if you add mynetwork.xx as "seach string" ( in Network settings : DNS :  Search domains). 

adding names and addresses in /etc/hosts on every ubuntumachine would work too - if you weren't using dhcp for the server (its common to give servers a static ip address)
192.168.1.1 tiger tiger.mynetwork.xx

An alternative is to run a WINS server (eg on the Windows machine, or from a Samba). WINS translates netbios names ("tiger") directly to IP addresses. I don't know if you'd require any additional configuration on the ubuntu machines but i suppose ubuntu's smbclient ("Samba client" can use WINS.

---

### Post by vairoj on 2007-02-09
The reason that the machine I was referring to uses dynamic address is they are more of a test machine (running under VMWare). We use it as a staging area for testing in web application and it is not always-on. I still prefer the dynamic IP approach if it is possible so it can be apply generally to all scenarios.

koenn's suggestion is exactly what I would like to accomplish. We have an active directory running so I assume the DNS server is running on the same box. After some experiment, I  just realized that there are problem with our DNS server setting. Currently, the DHCP setting pass 3 DNS server setting to DHCP clients, one is our internal DNS and the others are the ISP DNSes. It seems that this is not the correct way to do it because I can only use one of them at a time using this setting. For instance, if I move my internal DNS to the top, it can refer to all machine by both just name and fully-qualified name but can not access the Internet. If I move my ISP DNSes to the top, I could not ping our client by fully-qualified name.

By switching the order of DNS entry on the client, move the internal DNS server to the first, now Ubuntu client can ping Windows domain member machines, by both just name and fully-qualified name. So it turns out that this is not Linux specific issue, it is my server's DNS setting issue.

I believe once I solve the issue, everything would be working fine.

---

### Post by koenn on 2007-02-09
> **vairoj said:**
> 
one is our internal DNS and the others are the ISP DNSes. It seems that this is not the correct way to do it because I can only use one of them at a time using this setting. For instance, if I move my internal DNS to the top, it can refer to all machine by both just name and fully-qualified name but can not access the Internet. If I move my ISP DNSes to the top, I could not ping our client by fully-qualified name. 

It's more of a network design issue. 
Basically, the 3 DNS servers should offer the same functionality - the serve as fallback to each other : of one is unreachable or down, the others still provide dns service to your network. 

The quick and easy sollution (home/small business style) is as follows :
- let your network hosts use only your internal DNS server.
- add the external (ISP) DNS servers into the internal DNS server config as "forwarders"

That way, names on your LAN will be resolved by your DNS ; queries for names outside the LAN (eg internet) will be forwarded to the ISP DNS servers. 

Make sure there is no external access to your DNS server (firewall, ....) because attackers can mess with DNS to redirect your computers to places you don't want them to go. 

A more advanced sollution would using a second dns server as forwarder / dns caching proxy / ... , preferably in a DMZ.  But thats probably to much for what you're doing

---

### Post by vairoj on 2007-02-13
koenn, thanks for your explanation and recommendation. What I have just accomplished is exactly the way you described. Since it might be useful for other people, I will describe what I have done:

* Reconfigure Windows DNS server like koenn's suggestion. Instead of provide both internal DNS and ISP's DNSes through DHCP, only provide the internal DNS. And add external DNSes as forwarders. More info can be found at [http://support.microsoft.com/kb/825036](http://support.microsoft.com/kb/825036). From this step, I can ping Windows computers from both Windows and Linux clients using fully-qualified domain name and also access the Internet.

* Specify fully qualified domain name for Linux computers by editing /etc/hosts file. The fqdn must be the first entry on the line.

Example /etc/hosts file
```

127.0.0.1   tiger.example.com tiger localhost

```

* It seems that Ubuntu (Edgy in my case) does not register its hostname to DNS server by default (in contrast to Windows). This mean any other computers cannot access Ubuntu clients through fqdn. What I need to do is to /etc/dhcp3/dhclient.conf and uncomment this line:
```

send host-name "tiger.example.com";

```
This causes the machine to register its hostname to the DNS server, allowing other computers to refer to it by fqdn.

---

### Post by koenn on 2007-02-13
glad to see you figured out the details and got things working. 

one small comment:
> This causes the machine to register its hostname to the DNS server, allowing other computers to refer to it by fqdn.

I think "send hostname" sends the hostname to the **dhcp** server while the client requests an ip address from it. That way, the dhcp server knows both hostname and ip address, and can let the DNS server create a record for it. So the dhcp server updates the dns server.

It is possible to let the hosts create dns records directly, but that resuires they have write access to the dns server's zone files - which could be considered less secure.

---

### Post by vairoj on 2007-02-14
Yes, that sounds like a more correct explanation. Interestingly, it looks like [this issue is getting fixed]("https://bugs.launchpad.net/debian/+source/dhcp3/+bug/10239") now. So maybe in the future release of Ubuntu we would not require to manually edit this parameter anymore.

---

