---
title: "Slow connection at Ubuntu, help fast please"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Cene on 2006-11-16
Hi,

Everything worked fine until we got a new laptop, and a new modem with wlan along the laptop. Previous modem had no wlan, and laptop (using WinXP) was meant to connect thru wlan so we changed the modem to new one, Siemens SpeedStream 6515.

After installitation of it, everything works fine on laptop thru wlan, but my Ubuntu computer (connected by ethernet) is deadly slow. Loading of any page takes more than 15 seconds, some times even several minutes, even if the laptop is turned off (so wlan is not in use). Only modification I made to this system after installition of the new modem is that I installed Samba to transfer few files to Windows machine. It worked fine. Download speeds are normal (150 - 200 kb/s), and internet games etc. work fine. Only browsing the web is the problem.
I normally use Firefox, but problem exists with Opera too. Haven't tried other browsers.

Also, when I ping some well-known web server, first packet takes like 50 ms to complete, after it the readings are normal 10-15 ms. Noticed this with browsing too; if I connect to any site, it takes long to load the first page, but if i choose some link that leads to same server/domain, it loads that page normally. If I wait some time and  press the link after it, loading takes some time again.

I got another problem too. I got Apache installed, and would like that others would see the pages too. Apache is running and listening port 8181, but no one can access it. My IP responds to ping, but port 8181 won't. I've allowed all kind of connections to port 8181 from Firestarter. Also this worked well with old dsl box.

---

### Post by Cene on 2006-11-17
Sorry for early bump, but I'd really need help quickly. This is very annoying and I need to get my connection to work before saturday. :/

---

### Post by diepruis on 2006-11-17
Your first problem seems to be a DNS problem. Domain Name Service is the thing that resolves URLs into IP adresess that your computer can directly access. It seems yours is really slow, which might be caused by the settings on your modem.

I need to know what kind of modem this is. Is it a router with wlan that connects to your phone line, or a modem in a PC.

Also, please post the output of "dig".

For your second problem, are you acessing the page through DNS, or by using the IP directly? In both cases it should be [http://ip_or_hostname:8181](http://ip_or_hostname:8181). You might also have to bridge the port on the router, but without knowing how your network is set up, I can't help you.

---

### Post by Cene on 2006-11-17
> **diepruis said:**
> Your first problem seems to be a DNS problem. Domain Name Service is the thing that resolves URLs into IP adresess that your computer can directly access. It seems yours is really slow, which might be caused by the settings on your modem.
I've checked the settings at the modem and can't find anything that could cause this. Should i look for something specific in there?
> 
I need to know what kind of modem this is. Is it a router with wlan that connects to your phone line, or a modem in a PC.

Siemens SpeedStream 6515. It's external dsl box with wlan and 4 ethernet ports. Connected to phone line.
> 
Also, please post the output of "dig".

```

jhokkanen@vvivur:~$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18696
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       157495  IN      NS      J.ROOT-SERVERS.NET.
.                       157495  IN      NS      K.ROOT-SERVERS.NET.
.                       157495  IN      NS      L.ROOT-SERVERS.NET.
.                       157495  IN      NS      M.ROOT-SERVERS.NET.
.                       157495  IN      NS      A.ROOT-SERVERS.NET.
.                       157495  IN      NS      B.ROOT-SERVERS.NET.
.                       157495  IN      NS      C.ROOT-SERVERS.NET.
.                       157495  IN      NS      D.ROOT-SERVERS.NET.
.                       157495  IN      NS      E.ROOT-SERVERS.NET.
.                       157495  IN      NS      F.ROOT-SERVERS.NET.
.                       157495  IN      NS      G.ROOT-SERVERS.NET.
.                       157495  IN      NS      H.ROOT-SERVERS.NET.
.                       157495  IN      NS      I.ROOT-SERVERS.NET.

;; Query time: 51 msec
;; SERVER: 192.168.254.254#53(192.168.254.254)
;; WHEN: Fri Nov 17 14:57:12 2006
;; MSG SIZE  rcvd: 228

```

> 
For your second problem, are you acessing the page through DNS, or by using the IP directly? In both cases it should be [http://ip_or_hostname:8181](http://ip_or_hostname:8181). You might also have to bridge the port on the router, but without knowing how your network is set up, I can't help you.

I've triend both, by dns and IP directly. I can't get aswer either way. This doesnt work with my LAN ip either if i try it with the laptop.
This Ubuntu machine is connected by ethernet and laptop by wlan. They get ip's by dhcp.

---

### Post by diepruis on 2006-11-17
Mmmm... you seem to get a response from the root servers pretty quickly. Could you post "dig www.ubuntuforums.org" as well? Sorry, I should have asked earlier. I had a similiar problem and fixed it by following this howto: [http://ubuntuforums.org/showthread.php?t=181107](http://ubuntuforums.org/showthread.php?t=181107) and by setting my DNS to the freeDNS service: [http://www.opendns.com/](http://www.opendns.com/)

You might try those. I'm not sure what could be the cause other than a misconfigured/slow DNS server.

One more thing, is apt-get / aptitude also very slow in updating? Does it take an age to move from 0% for each server?

---

### Post by Cene on 2006-11-17
> **diepruis said:**
> Mmmm... you seem to get a response from the root servers pretty quickly. Could you post "dig www.ubuntuforums.org" as well? Sorry, I should have asked earlier. I had a similiar problem and fixed it by following this howto: [http://ubuntuforums.org/showthread.php?t=181107](http://ubuntuforums.org/showthread.php?t=181107) and by setting my DNS to the freeDNS service: [http://www.opendns.com/](http://www.opendns.com/)> 
[code]
jhokkanen@vvivur:~$ dig www.ubuntuforums.org

; <<>> DiG 9.3.2 <<>> www.ubuntuforums.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38445
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.ubuntuforums.org.          IN      A

;; ANSWER SECTION:
www.ubuntuforums.org.   1574    IN      A       82.211.81.186

;; Query time: 23 msec
;; SERVER: 192.168.254.254#53(192.168.254.254)
;; WHEN: Fri Nov 17 15:30:36 2006
;; MSG SIZE  rcvd: 54

Noticed same thing here that i found out with ping. Everything works fine if you ping it, but when you try to load that page, it's really slow.
[quote]
You might try those. I'm not sure what could be the cause other than a misconfigured/slow DNS server.

One more thing, is apt-get / aptitude also very slow in updating? Does it take an age to move from 0% for each server?
How can I start using that OpenDNS then? Create an account, then what?
And yes, apt is a bit slow connecting too. Not as slow as Firefox tho.

---

### Post by diepruis on 2006-11-17
You don't need to get an account, just follow the instructions. You'll probably need to setup your router as well, setting the DNS server in there. Be warned though: you might break something, so remember what you change - write it down. The instructions are [here](http://www.opendns.com/start) BTW. Oh, and try the firefox optimisations as well.

---

### Post by Cene on 2006-11-17
> **diepruis said:**
> You don't need to get an account, just follow the instructions. You'll probably need to setup your router as well, setting the DNS server in there. Be warned though: you might break something, so remember what you change - write it down. The instructions are [here](http://www.opendns.com/) BTW. Oh, and try the firefox optimisations as well.

Uhm.. Ok, I found the instructions, but what should I put to "IP Address" field on the modem setup?

---

### Post by diepruis on 2006-11-17
> **Cene said:**
> Uhm.. Ok, I found the instructions, but what should I put to "IP Address" field on the modem setup?

I don't think you need to change that. As long as you set the Primary and Secondary DNS fields that shouldn't be a problem.

---

### Post by Cene on 2006-11-17
> **diepruis said:**
> I don't think you need to change that. As long as you set the Primary and Secondary DNS fields that shouldn't be a problem.
I need to enter something there. Otherwise it won't accept my settings and reverts back to old ones with an error message.

---

### Post by diepruis on 2006-11-17
Mmmm... I need the context of that box... could you take a screenshot (press the Print Screen button on your keyboard) and email it to me? I'll PM you my email adress.

---

### Post by Cene on 2006-11-17
I sent you that mail some time ago already. But I found out myself that what I should put in there. Only problem was that I couldnt establish any connection to Internet before I enable dhcp again. So OpenDNS won't work either, or i screwed something up.

---

### Post by diepruis on 2006-11-17
DHCP shouldn't influence your DNS. Where did you enable DHCP? Did you try rebooting everything (router, pc)? Could you post the output of ifconfig and dig please? Also, check if all the settings are still there after you rebooted the router.

---

### Post by Cene on 2006-11-17
> **diepruis said:**
> DHCP shouldn't influence your DNS. Where did you enable DHCP?
By the router settings. It has an switch for DHCP or  "manual" settings, including DNS server. Can't select both.
> 
Did you try rebooting everything (router, pc)?

Yes.
> Could you post the output of ifconfig and dig please?
With DHCP:
```

jhokkanen@vvivur:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:69:35:B6  
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe69:35b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128040770 (122.1 MiB)  TX bytes:15428929 (14.7 MiB)
          Interrupt:201 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:733814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:733814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51015614 (48.6 MiB)  TX bytes:51015614 (48.6 MiB)

```
```

jhokkanen@vvivur:~$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60353
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;.                              IN      NS

;; ANSWER SECTION:
.                       518154  IN      NS      L.ROOT-SERVERS.NET.
.                       518154  IN      NS      M.ROOT-SERVERS.NET.
.                       518154  IN      NS      A.ROOT-SERVERS.NET.
.                       518154  IN      NS      B.ROOT-SERVERS.NET.
.                       518154  IN      NS      C.ROOT-SERVERS.NET.
.                       518154  IN      NS      D.ROOT-SERVERS.NET.
.                       518154  IN      NS      E.ROOT-SERVERS.NET.
.                       518154  IN      NS      F.ROOT-SERVERS.NET.
.                       518154  IN      NS      G.ROOT-SERVERS.NET.
.                       518154  IN      NS      H.ROOT-SERVERS.NET.
.                       518154  IN      NS      I.ROOT-SERVERS.NET.
.                       518154  IN      NS      J.ROOT-SERVERS.NET.
.                       518154  IN      NS      K.ROOT-SERVERS.NET.

;; Query time: 153 msec
;; SERVER: 192.168.254.254#53(192.168.254.254)
;; WHEN: Fri Nov 17 17:25:15 2006
;; MSG SIZE  rcvd: 228

```

With OpenDNS (no DHCP):
```

jhokkanen@vvivur:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:69:35:B6  
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe69:35b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128427259 (122.4 MiB)  TX bytes:15568755 (14.8 MiB)
          Interrupt:201 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:735543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:735543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51135006 (48.7 MiB)  TX bytes:51135006 (48.7 MiB)

```
```

jhokkanen@vvivur:~$ dig

; <<>> DiG 9.3.2 <<>>
;; global options:  printcmd
;; connection timed out; no servers could be reached

```

As you can see, no connection without DHCP.


> Also, check if all the settings are still there after you rebooted the router.
Yes they are.

---

### Post by diepruis on 2006-11-17
> **Cene said:**
> By the router settings. It has an switch for DHCP or  "manual" settings, including DNS server. Can't select both.


Damn. That's retarded.

You can try the instructions [here]("http://www.opendns.com/start/unix.php") to set it up on only your PC.

---

### Post by Cene on 2006-11-17
> **diepruis said:**
> Damn. That's retarded.

You can try the instructions [here]("http://www.opendns.com/start/unix.php") to set it up on only your PC.

Thank you. That helped a bit. I mean, the internet is now atleast browsable. ^^
It's still slower than with the previous box and takes still some time to connect to sites wich worked flawlessly with old box, while others are loaded instantly, just like before.

Any ideas on Apache problem?

---

### Post by diepruis on 2006-11-17
No problem. Did you try the firefox stuff?

I'll get back to you on apache in a while. I'm a bit busy right now. =D

---

### Post by Cene on 2006-11-17
> **diepruis said:**
> No problem. Did you try the firefox stuff?

I'll get back to you on apache in a while. I'm a bit busy right now. =D

Yes, I made the firefox thingies too. That was some help too, i think. ^^

I don't know the words to thank you enough for helping me. Couldnt think that just changing an dsl box can be such a pain. :D

---

### Post by diepruis on 2006-11-18
> **Cene said:**
> Yes, I made the firefox thingies too. That was some help too, i think. ^^

I don't know the words to thank you enough for helping me. Couldnt think that just changing an dsl box can be such a pain. :D

No problem :) I'd advise you to read carefully through any of your router's documentation you can find, there might be something more in there, or something to fix your apache. I'm playing with apache myself, so if I stumble onto something I'll let you know.

Good luck =D

---

### Post by Cene on 2006-11-18
> **diepruis said:**
> No problem :) I'd advise you to read carefully through any of your router's documentation you can find, there might be something more in there, or something to fix your apache. I'm playing with apache myself, so if I stumble onto something I'll let you know.

Good luck =D

Ok, found out something really strange. o_O
I can't access apache or SSH by this computer (using my DNS, WAN ip or LAN ip), and neither by laptop. Everyone else is ablo to connect my apache and ssh without problems though. Wtf? :D

Hosts.allow, hosts.deny, apache configs and OpenSSH configs are correct, so I don't know where the problem could be.

---

### Post by Cene on 2006-11-21
Anyone? :p

---

### Post by diepruis on 2006-11-21
Just a quick thought: have you checked the firewalls on the client PCs?

---

### Post by Cene on 2006-11-21
Huh? :p
I use Firestarter on Ubuntu box, port 8181 (what Apache is listening) allowed on both directions (in and out). On laptop I use ZoneAlarm (laptop is running WinXP).

People who can connect are my friends who are not in same network. Dunno what firewalls they use. :p

---

### Post by lonetree on 2006-11-21
Hi Cene,

how did your friend get connected to your web server? 

[http://hostname_or_wanip:8181](http://hostname_or_wanip:8181) ?

or simply without the 8181?

---

### Post by Cene on 2006-11-21
With :8181. Otherwise it connects to port 80 no? My router's configuration server for lan is at port 80. :)

---

### Post by lonetree on 2006-11-22
Hi Cene,

you will have to do port forwarding in your router to point to your web server at port 8181. Also, it is a good idea to make your web server a static IP address, else if there is any change to the IP address of your web server, it will not be accessable from the outside world. Hope this help a little.

regards,

---

### Post by Cene on 2006-11-22
> **lonetree said:**
> Hi Cene,

you will have to do port forwarding in your router to point to your web server at port 8181.

How do I do that? Can't find anything from router's setup. :|

> Also, it is a good idea to make your web server a static IP address, else if there is any change to the IP address of your web server, it will not be accessable from the outside world.

I know, already got one. :)

---

### Post by compwiz18 on 2006-11-22
if you haven't gotten your internet slowness fixed, it sounds like you have an IPv6 problem.  Try adding IPv6 to the bottom **/etc/modprobe.d/blacklist** and reboot.  Internet should be fast now :D

---

### Post by lonetree on 2006-11-22
[QUOTE=Cene;1792024]How do I do that? Can't find anything from router's setup. :|

May I ask what router are you using? I may be able to figure out. For myself, I am using a dlink which port forwarding resides in |Advance (tab) | Virtual Server |. Let me know the make of your router. I wish I could help you with this. 

As for your slowness, probably you could look at the ubuntu guide for tweaking firefox 
[http://ubuntuguide.org/wiki/Dapper#How_to_load_Web_site_faster_in_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_load_Web_site_faster_in_Mozilla_Firefox)

regards,

[Edit]

Sorry, i overlook on the router you are using, although I couldn't find the exact type of router you are using, I found this model which you might want to take a look,maybe speedstream 6515 may look similar 
[http://portforward.com/english/routers/port_forwarding/Efficient-Siemens/Speedstream-5100/GameSpy_Arcade.htm](http://portforward.com/english/routers/port_forwarding/Efficient-Siemens/Speedstream-5100/GameSpy_Arcade.htm)

---

### Post by Cene on 2006-11-22
> **lonetree said:**
> [QUOTE=Cene;1792024]How do I do that? Can't find anything from router's setup. :|

May I ask what router are you using? I may be able to figure out. For myself, I am using a dlink which port forwarding resides in |Advance (tab) | Virtual Server |. Let me know the make of your router. I wish I could help you with this. 

As for your slowness, probably you could look at the ubuntu guide for tweaking firefox 
[http://ubuntuguide.org/wiki/Dapper#How_to_load_Web_site_faster_in_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_load_Web_site_faster_in_Mozilla_Firefox)

regards,

[Edit]

Sorry, i overlook on the router you are using, although I couldn't find the exact type of router you are using, I found this model which you might want to take a look,maybe speedstream 6515 may look similar 
[http://portforward.com/english/routers/port_forwarding/Efficient-Siemens/Speedstream-5100/GameSpy_Arcade.htm](http://portforward.com/english/routers/port_forwarding/Efficient-Siemens/Speedstream-5100/GameSpy_Arcade.htm)[/QUOTE]

Network slowness is already solved. 

I followed those instructions, and forwarded port 8181 to my ip. Still can't connect myself.

---

### Post by lonetree on 2006-11-22
Hi Cene,

can you change your port to 80 or 8080 instead? Give a try and see if this is port problem or router or your web server problem. Don't forget to change your port forwarding in the router if you change to 80 or 8080.

Try it, test it and let me know, I suspect port 8181 may be the cause, can't be that sure as I have never used 8181 before. I did a bit of goggling for this port.

[http://www.google.com.sg/search?q=port+8181&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com.sg/search?q=port+8181&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a)

[http://www.iss.net/security_center/advice/Exploits/Ports/8181/default.htm](http://www.iss.net/security_center/advice/Exploits/Ports/8181/default.htm)

Hope it helps you.

By the way, how did you solve the internet slowness problem?


regards,

---

### Post by Cene on 2006-11-22
> **lonetree said:**
> Hi Cene,

can you change your port to 80 or 8080 instead? Give a try and see if this is port problem or router or your web server problem. Don't forget to change your port forwarding in the router if you change to 80 or 8080.

Try it, test it and let me know, I suspect port 8181 may be the cause, can't be that sure as I have never used 8181 before. I did a bit of goggling for this port.

[http://www.google.com.sg/search?q=port+8181&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com.sg/search?q=port+8181&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a)

[http://www.iss.net/security_center/advice/Exploits/Ports/8181/default.htm](http://www.iss.net/security_center/advice/Exploits/Ports/8181/default.htm)

Hope it helps you.

Didn't help. It have always been at port 8181 with old router too and worked fine.

> 
By the way, how did you solve the internet slowness problem?



Switched to [OpenDNS](http://www.opendns.com/). Dunno what in it actually helped, when the laptop works fine with my ISP's default DNS. Most important is that it works now tho. :p

---

### Post by diepruis on 2006-11-22
> **Cene said:**
> Dunno what in it actually helped, when the laptop works fine with my ISP's default DNS. Most important is that it works now tho. :p

According to OpenDNS, this is because they have particularly large caches. I think it's because they actually give a crap.

[EDIT] Just a quick mention: I must connect to apache by my local IP or by using localhost:port. You can't use the outside (WAN) address.

---

### Post by Cene on 2006-11-23
> **diepruis said:**
>  Just a quick mention: I must connect to apache by my local IP or by using localhost:port. You can't use the outside (WAN) address.

..why? My local ip and localhost:8181 works also, but can't connect by [http://my_wan_ip:8181](http://my_wan_ip:8181), when it works to other people.

---

### Post by diepruis on 2006-11-23
> **Cene said:**
> ..why? My local ip and localhost:8181 works also, but can't connect by [http://my_wan_ip:8181](http://my_wan_ip:8181), when it works to other people.

To tell you the truth: I have no idea why. I'd love it if someone could explain why.

---

