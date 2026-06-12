---
title: "Hostname doesn't work anymore"
date: 2015-02-20
forum: Networking &amp; Wireless
---

### Post by RedXon on 2015-02-20
Hy

I have a problem with my Ubuntu Server 14.10.

The thing is, the server has the hostname server.local since forever. And everything worked just fine, I could access it with every browser just by going to server.local:8080 or whatever port I wanted to.

The thing is, it doesn't work anymore and I have no idea why. I didn't change the hostname, in fact I didn't change anything at all, but still, when I want to go to server.local (on any port, even 22 for ssh) it just doesn't see the server, as if the hostname was not there anymore. I can connect it just fine by entereing it's IP, but I'd really prefer using the hostname again.

Now I have noticed the strangest thing, when I do that from a PC (I have tried 3 different PCs) with whatever browser it doesn't work. But I can still connect fine with my iPhone and iPad. So what could be the problem here=

Thanks

---

### Post by steeldriver on 2015-02-20
Hello and welcome to the forums

"it doesn't work anymore" doesn't really  give us much to work with: what happens,  exactly? what error messages do you get (in the browser - and from ssh)? or does it just hang/timeout? what happens if you ping by hostname.local?

If it works from other devices, then it sounds like a problem with the name resolution configuration of the 3 *client* PCs (or your router). What OS are they running?

---

### Post by RedXon on 2015-02-20
Well doesn't work means what I've written, they get no connection (in Putty I get "Host not found" and in chrome I get "ERR_NAME_RESOLUTION_FAILED")

So I don't believe, that the error is with the PCs (it worked 3 days ago) and since then I haven't changed anything in the configuration. All the PCs are running Windows 8.1(.1).
It could be an issue with the server updating some package (I don't know). I always do all the updates, I logon about twice a week via SSH to check for updates and do "sudo apt-get upgrade". 

I'm not an expert with this, but doesn't windows need another way to resolve the hostname to the IP than Linux and Unix devices? And the DNS Server for the local network is the router, so that could also be an issue. But then again, I haven't changed anything in the configuration of the router. So really, the only thing I did was update the packages on the router. My router is a Netgear R7500.

External access also works good via the DynDNS url I have (just not from home, because my router doesn't support loopback) so this is not an issue. It's really just the fact, that all my windows PCs don't seem to resolve the hostname of the server anymore, when other devices still do that... It's btw also not a browser Issue (I get a Page can not be displayed error in Internet Explorer).

So what do you think? I mean I really don't think that all of the 3 PCs suddenly decide to have a name resolution issue (also because I have done Windows Updates on 2 of them, but not on the third, so I can also rule out, that an update on Windows causes this...)

---

### Post by RedXon on 2015-02-24
Seriously? No one has any Ideas?

Comeon I can't be the only one that has this problem, because obviously it came with an update in ubuntu. I mean I have set up a fresh installation of windows and it didn't work. It worked in Ubuntu, iOS and Debian, so clearly there has to be something wrong with the way ubuntu configures its hostname. And then again it can't be the router because that one hasn't changed at all and second of all it wouldn't work with other devices either if the router was the problem. And then again, not the router manages the hostnames, it's the server who does that.

---

### Post by steeldriver on 2015-02-24
I don't really know what to suggest - the next things I'd look at if it were my system are the clients' nsswitch.conf files

```

cat /etc/nsswitch.conf

```
and the response from
```

avahi-resolve-host-name -v server.local

```

---

### Post by bab1 on 2015-02-24
> **RedXon said:**
> Seriously? No one has any Ideas?

Comeon I can't be the only one that has this problem, because obviously it came with an update in ubuntu. I mean I have set up a fresh installation of windows and it didn't work. It worked in Ubuntu, iOS and Debian, so clearly there has to be something wrong with the way ubuntu configures its hostname. And then again it can't be the router because that one hasn't changed at all and second of all it wouldn't work with other devices either if the router was the problem. And then again, not the router manages the hostnames, it's the server who does that.

Are you saying that the OTHER hosts can't resolve the hostname of your server?  I assume this server is an Ubuntu OS machine.  Not that it matters.  No host broadcasts it's hostname (DNS).  Name resolution is handled by a DNS server.  If you have local LAN DNS issues then you need to check the local DNS server setup.

Bottom line if you are having DNS problems, look to where the DNS settings are, not the "lost" host.

As a separate issue, all Ubuntu hosts check their local /etc/hosts file before asking for DNS server information.  What do you get from the servers CLI to this command```
ping <server_name> 
```...where <server_name> is the hostname of that host.

---

### Post by RedXon on 2015-02-28
Okay, let's see... Yes I'm runnung Ubuntu 14.10 Server

When I try to ping the server, I get various results for obvious reasons. From every Windows client in my network I just get a Host not found error.
From my other ubuntu machine it resolves the host correctly to the local IP (192.168.0.13) and the Pings work just fine.

My (local) DNS Server is my router on 192.168.0.1. The router obviously then has another DNS Server from the provider for the internet.

The crazy thing is, that I have no Idea why it not working anymore from Windows pcs. I mean, I didn't change anything in the server, I didn't change anything in the router and I didn't change anything in windows, it just suddenly stopped working, that's why my guess was, that the problem was an update on the server. 

What I don't really know how it works is the hostname resolution order. At the moment it is set to:
```
files mdns4_minimal [NOTFOUND=return] dns
```

I haven't changed this but I guess it could be the reason it doesn't work anymore. I googled and tried to change it to NOTFOUND=continue but it hasn't helped. But maybe someone can confirm or deny, that the resolution order is important and could be the problem here.

---

### Post by bab1 on 2015-02-28
> **RedXon said:**
> Okay, let's see... Yes I'm runnung Ubuntu 14.10 Server

When I try to ping the server, I get various results for obvious reasons. From every Windows client in my network I just get a Host not found error.
From my other ubuntu machine it resolves the host correctly to the local IP (192.168.0.13) and the Pings work just fine.

My (local) DNS Server is my router on 192.168.0.1. The router obviously then has another DNS Server from the provider for the internet.

The crazy thing is, that I have no Idea why it not working anymore from Windows pcs. I mean, I didn't change anything in the server, I didn't change anything in the router and I didn't change anything in windows, it just suddenly stopped working, that's why my guess was, that the problem was an update on the server. 

What I don't really know how it works is the hostname resolution order. At the moment it is set to:
```
files mdns4_minimal [NOTFOUND=return] dns
```

I haven't changed this but I guess it could be the reason it doesn't work anymore. I googled and tried to change it to NOTFOUND=continue but it hasn't helped. But maybe someone can confirm or deny, that the resolution order is important and could be the problem here.
The nsswitch.conf file is correct and is not your problem.  The problem is not with the Ubuntu server at all.  The *other* hosts DO NOT use the servers nsswitch.conf file to resolve DNS.  That file is for the server to use for it's own resolution needs.

---

### Post by RedXon on 2015-02-28
So you suppose, that the issue lies in the router itself? Now, where could that problem be? I do not recall changing anything within the router configuration and also I did not find any setting within the router to change the behaviour of the DNS server. As I mentioned, only Windows clients have this problem. The Router is a Netgear R7500 and the firmware is [RIGHT][COLOR=#000000][FONT=Arial][B]V1.0.0.82.

[/B][/FONT][/COLOR][/RIGHT]Or do you believe, that i should post this problem in the Netgear forum? DO you think I would have better changes of getting a solution there?

---

### Post by bab1 on 2015-02-28
> **RedXon said:**
> So you suppose, that the issue lies in the router itself? Now, where could that problem be? I do not recall changing anything within the router configuration and also I did not find any setting within the router to change the behaviour of the DNS server. As I mentioned, only Windows clients have this problem. The Router is a Netgear R7500 and the firmware is [RIGHT][COLOR=#000000][FONT=Arial][B]V1.0.0.82.

[/B][/FONT][/COLOR][/RIGHT]Or do you believe, that i should post this problem in the Netgear forum? DO you think I would have better changes of getting a solution there?
I never guess anything.  I would test and find the exact problem.  Can the Windows machine ping the Ubuntu server by IP Address?

To ping a host by DNS name (hostname) the pinging machine first queries A DNS server to resolve the hostname to the IP Address.  What DNS server do your Windows machines use?

You can [follow this]("http://www.windowsnetworking.com/articles-tutorials/trouble/10-Ways-Troubleshoot-DNS-Resolution-Issues.html") to see what your Windows settings are.  What DNS server are the Windows machines configured to use?

---

### Post by steeldriver on 2015-02-28
I don't think you showed us the output of 

```

avahi-resolve-host-name -v server.local

```

yet (where 'server' is replaced by the actual server name)

---

### Post by bab1 on 2015-02-28
> **steeldriver said:**
> I don't think you showed us the output of 

```

avahi-resolve-host-name -v server.local

```

yet (where 'server' is replaced by the actual server name)

+1

A good point.  I forgot about the .local domain.  However avahi is not part of the Windows system.  Windows has ZeroConf which is the same thing. The OP can read about ZeroConf (Bonjour) [here]("http://en.wikipedia.org/wiki/Bonjour_%28software%29#Microsoft_Windows_implementation").

[COLOR="#0000FF"]Edit:  In any case it is a Windows request for a name mapping for the server.[/COLOR]

---

### Post by RedXon on 2015-03-01
All right. So first thing's first, the output of the avahi-resolve-host...
```

marco@Server:~$ avahi-resolve-host-name -v server.local
Server-Version: avahi 0.6.31; Rechnername: Server.local
Server.local    fe80::eea8:6bff:fefd:7772

```

The output of Windows Ping for the Hostname: (Sorry, it's german but basicly means Host not found.)
```

C:\Users\Marco>ping server.local
Ping-Anforderung konnte Host "server.local" nicht finden. Überprüfen Sie den Namen, und versuchen Sie es erneut.



```

Output for IP-Ping:
```

C:\Users\Marco>ping 192.168.0.13
Ping wird ausgeführt für 192.168.0.13 mit 32 Bytes Daten:
Antwort von 192.168.0.13: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.13: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.13: Bytes=32 Zeit<1ms TTL=64
Antwort von 192.168.0.13: Bytes=32 Zeit<1ms TTL=64

```

And finally, the ipconfig output from windows on the active conection: (I deleted some Infos I did not want to share)
```

Ethernet-Adapter Ethernet 2:


   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Thinkpad USB 3.0 Ethernet Adapter
   Physische Adresse . . . . . . . . : ....
   DHCP aktiviert. . . . . . . . . . : Ja
   Autokonfiguration aktiviert . . . : Ja
   Verbindungslokale IPv6-Adresse  . : fe80::a95e:c748:b054:904b%10(Bevorzugt)
   IPv4-Adresse  . . . . . . . . . . : 192.168.0.16(Bevorzugt)
   Subnetzmaske  . . . . . . . . . . : 255.255.255.0
   Lease erhalten. . . . . . . . . . : Sonntag, 1. März 2015 19:43:13
   Lease läuft ab. . . . . . . . . . : Montag, 2. März 2015 19:43:12
   Standardgateway . . . . . . . . . : 192.168.0.1
   DHCP-Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6-IAID . . . . . . . . . . . : 322705568
   DHCPv6-Client-DUID. . . . . . . . : 00-01-00-01-1C-76-6C-E0-00-00-00-00-00-00


   DNS-Server  . . . . . . . . . . . : 192.168.0.1
   NetBIOS über TCP/IP . . . . . . . : Aktiviert



```

So finally, I think that should be all the information needed. And honestly I do not see anything here that is configured wrong. 


Oh btw: because it was in the link you sent me I've checked this too: nslookup with anything works (from 192.168.0.1) except of course for the server.local domain.
And the DNS Servers for external configuration are configured correctly in the router (and I can ping them without a problem.)

---

### Post by steeldriver on 2015-03-01
Hmm... the server's avahi-daemon appears to only be advertising its IPv6 link-local address: what does

```

grep '^use' /etc/avahi/avahi-daemon.conf

```

on the server say? what happens if you

```

ping **-6** server.local

```
from the Windows box?

---

### Post by RedXon on 2015-03-02
ok...
```

marco@Server:~$ grep '^use' /etc/avahi/avahi-daemon.conf
use-ipv4=yes
use-ipv6=yes

```

And ping -6 doesn't work. Same result as the normal ping.

---

