---
title: "Dns working weird at /etc/resolv.conf"
date: 2019-02-25
forum: Networking &amp; Wireless
---

### Post by neo.linux on 2019-02-25
Hi, 
I am a newbie in terms of others present here . But I have little knowledge of linux and trying to enhance it more on the go. 
The situation that I am facing is when I change the nameserver setting at /etc/resolv.conf to any random ip ( other than local dns server or known public dns servers) it still resolves the request and I am being able to browse the internet without any glitch.

Ideally it should block access to the internet if the nameserver isn't a valid dns server.

I checked this anomaly both with NetworkManager as well as Wicd connection manager on ubuntu 18.04.2 LTS

So instead of nameserver 8.8.8.8 if I put nameserver x.x.x.x ( where x is random numbers ) it still resolves all the requests my client make.

Earlier when I had used ubuntu 16.04 or ubuntu 17.04 , I never noticed this anomaly and my internet would stop if I changed the nameserver to a dns server that is not active.

IF I am missing out some thing , please let me understand . 

Thanks

---

### Post by chili555 on 2019-02-25
That suggests that dnsmasq is working as expected. [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

> 
A local DNS cache can speed up internet browsing because the user's browser will not need to access a domain name server when it looks up a domain name the computer has visited before.
If you are accessing a site that you've previously visited, dnsmasq checks your local cache to see if it has the IP address by number; for example, [www.ubuntu.com](www.ubuntu.com) is 91.189.89.118. If that number is stored, it simply goes there.

If the number is not stored, then and only then, does your computer ask the listed DNS nameserver for the information.

The behavior you describe is entirely normal and expected.

---

### Post by neo.linux on 2019-02-26
Thanks for providing insight to the matter at hand. I understand what you say , but tweaking some of the dns setup which should make the system use one of the listed nameservers, it still doesn't change anything. From your suggestion , I felt flushing the local dns cache will reset dns cache and it will start resolving the requests from the listed nameservers. Here I want to note that my system doesn't have dnsmasq installed . 

Also I tried flushing the local dns cache using the following commands 

1. sudo /etc/init.d/dns-clean restart
2. sudo /etc/init.d/networking force-reload


After running the above step , I ran the nslookup command to check if it still resolves using a random ip address which is not an active dns server and to my surprise , I am still able to browse the internet and nslookup/dig commands return valid results.

I am at a fix and wit's end.

I can provide screen shots to prove my situation . 

Please help. I need a solution to this as  I want to test a dns server on a vps and want my machine to react to it .


P:S or is it because of rhe router has dns caching enabled ?

---

### Post by chili555 on 2019-02-26
> want to note that my system doesn't have dnsmasq installed . How is this possible? Did you take affirmative steps to remove it? What does this tell us?```
sudo updatedb && locate dnsmasq
```

If you have Network Manager installed, it is far easier and certainly persistent to make the change there. 

[IMG]https://www.liberiangeek.net/wp-content/uploads/2013/03/google_dns_provider_1_thumb.png[/IMG]

I suppose that it's possible that your router does DNS caching.

Please be aware the /etc/resolv.conf isn't an actual file; it's a symbolic link. If you add DNS namesevers to it and reboot, it will be rewritten.> I checked this anomaly both with NetworkManager as well as Wicd connection manager on ubuntu 18.04.2 LTSI have never seen any problem that was solved by using Wicd instead of NM.

---

### Post by neo.linux on 2019-02-27
Thank you Chili555 for your reply but
I still didn't get rid of the problem. I  understood few things and configured netplan's yaml file how it supposed to be with NetworkManager and then changed the DNS servers(In this case I changed it to 9.9.9.9 - which is a public dns server) under the NM panel. Rebooted the system. Under the NM panel for the specified DNS server shows up But upon resolving with nslookup it doesn't show up the specified DNS server as the one resolving the dns request.
For example if I am trying to resolve [www.hotmail.com]("http://www.hotmail.com") with # nslookup [www.hotmail.com]("http://www.hotmail.com") ,  it returns 
Server:        127.0.0.53
Address:    127.0.0.53#53

Non-authoritative answer:
[www.hotmail.com]("http://www.hotmail.com")    canonical name = outlook-fd-0010.live.com.
outlook-fd-0010.live.com    canonical name = a-0010.a-msedge.net.
Name:    a-0010.a-msedge.net
Address: 204.79.197.212
Name:    a-0010.a-msedge.net
Address: 2620:1ec:c11::212


It should have returned 9.9.9.9 as the resolving dns server.
I fail to understand this . 

Also while searching further for a solution I found this thread ( [https://ubuntuforums.org/showthread.php?t=2403929](https://ubuntuforums.org/showthread.php?t=2403929) ) where you had also participated and the OP seemed to have solved his problem and have provided the solution.Alas when I followed his solution , the entire internet stopped working . I had to undo the steps to get it back working

No this another thing that I noticed . IF on the NetworkManager panel , I change my DNS to an invalid ip or an ip that is not active as of now  and I make a DNS request, the system still resolves using the local caching nameserver. 

Ain't it supposed to block connection to the internet outside the LAN if the DNS is an invalid one ?
Really can't understand how it works,

I need to know this as my test involves to route all dns requests to route through the dns server I  provide under NetworkManager.
and block all requests  when the dns is changed to something else.

Please advice.

---

### Post by chili555 on 2019-02-27
> For example if I am trying to resolve [www.hotmail.com](www.hotmail.com) with # nslookup [www.hotmail.com](www.hotmail.com) , it returns 
Server: 127.0.0.53 [COLOR="#FF0000"]<-- Hey, we have the address in our cache; no need to look elsewhere![/COLOR]
Address: 127.0.0.53#53
What does this tell us?```

nmcli device show wlp3s0 | grep IP4.DNS

```Please substitute your relevant interface if not wlp3s0. That should tell you the fall-back DNS nameserver if dnsmasq doesn't have the address in cache.

---

### Post by neo.linux on 2019-02-27
I understood and yeah the relevant interface i.e wlp2s0 shows the desired dns server I wanna use . I flush using - systemd-resolve --flush-caches and then restart the systemd resolver with systemctl restart systemd-resolved.service so that the dns cache is cleared. Ideally in this situation if I use a invalid dns at wlp2s0 , no traffic should resolve right . 

I did all that and then again when i try to resolve a domain that I have never used in my entire life on this system , resolves and shows 

Server: 127.0.0.53 [COLOR=#FF0000]<-- Hey, we have the address in our cache; no need to look elsewhere!  . Wasn't this flushed in the previous commands . ? 


I am at a total loss yet again . I could fix the desired dns server to the interface of my choice . I want it to act like this . Flush the local cache , and use a desired dns to that it blocks all traffic if it doesn't find the desired dns as the resolver 

Thanks again for your patience and endeavor
Waiting for a reply 
[/COLOR]

---

### Post by chili555 on 2019-02-27
All I can therefore suspect is the router cache. Sorry.

---

