---
title: "Allow Network Computer To Access System Via Internet"
date: 2016-09-12
forum: Networking &amp; Wireless
---

### Post by tcmtrinity on 2016-09-12
Hiya,

I've been trying for a while now to allow my network computers to access my linux box via the net. They are all on the Lan together, and they can all access the system via the lan. But the moment a connection goes out to the net and comes back it's can't connect. For some game sever testing I need to be able to have computers on my lan connect to the linux box via the net like other people would. I can connect to the HTTP server on the linux machine if I use Tor, so it would seem like the machine simply doesn't like the loopback feel of it all.

T

---

### Post by TheFu on 2016-09-13
Welcome to the forums.

Some routers prevent connections to the WAN interface from inside the LAN. Some let us disable this "protection" and others do not.  Check the documentation for your router (or firmware). There are some unusual attack vectors that the routers are blocking. Some ISPs block ports too - like CIFS, telnet, and on residential connections, FTP. Could be any of those things.

What protocol is the "game server" using?  Also, can you clarify the following:
* What exactly do you mean by cannot connect?  
* Which ports and protocols?  
* What is the network topology? 
* Is there a router? 
* Is it doing NAT or not? 
* Does the Linux system have a static LAN IP? 
* Are the correct ports forwarded on the router for the WAN port to the correct LAN port?  
* Do you use port-translation?

Does ssh work both internally and through the WAN interface?  That's the first thing I setup.

Would be good to also understand your level of expertise with Linux and networking. That will let us reply with the most useful information.

---

### Post by tcmtrinity on 2016-09-13
> **TheFu said:**
> Welcome to the forums.

Some routers prevent connections to the WAN interface from inside the LAN. Some let us disable this "protection" and others do not.  Check the documentation for your router (or firmware). There are some unusual attack vectors that the routers are blocking. Some ISPs block ports too - like CIFS, telnet, and on residential connections, FTP. Could be any of those things.

What protocol is the "game server" using?  Also, can you clarify the following:
* What exactly do you mean by cannot connect?  
* Which ports and protocols?  
* What is the network topology? 
* Is there a router? 
* Is it doing NAT or not? 
* Does the Linux system have a static LAN IP? 
* Are the correct ports forwarded on the router for the WAN port to the correct LAN port?  
* Do you use port-translation?

Does ssh work both internally and through the WAN interface?  That's the first thing I setup.

Would be good to also understand your level of expertise with Linux and networking. That will let us reply with the most useful information.

Linux Experience is pretty much nill.

I am using a router, and have all ports forwarded. The servers I am testing atm are Ark - Steam. I also have TeamSpeak and Minecraft servers running. People can connect via the internet, but I have to use Lan or it won't connect. 

Lan Ip is static and is not using port translation.

By cannot connect I mean there is no difference if the machine is powered down it is literally like it isn't there when I try to connect.

Network config is simple. All systems are DHCP except the linux server which is static IP. Using TCP & UDP which are forwarded in the router.

I am also running HTTP for a web server on the linux box (NGINX). Everyone external can access it, but I am getting 400 bad request unless I access it via Lan.

All of these servers work for everyone outside the house. And they all work for me if I connect via Lan, but nothing works for me if I try to connect via my external IP.


Sorry if some of that is repeating. I've used linux primarily for game & ts serving and don't know more than what I've hobbled together to make it work. The killer is that I need to be able to connect my computer to the server via my external IP not my just internal IP.

Oh, from the server itself I can access the servers via both internal & external IP. But to acheive this I had to add this to the Hosts file:
```

127.0.1.1     mymachinename
127.0.0.1     mysubdomain.mydomain.com

```

---

### Post by TheFu on 2016-09-13
> have all ports forwarded

I hope not.  Only the required ports should be forwarded, not all of them. These words can have multiple meanings. Please clarify.

Used to run a TF server back in the early 2000s, just needed to get the correct ports for it to work.

From what I'm reading, it appears things are working as designed and just a little more understanding of networking, name resolution and DNS is needed on your part.  There is a podcast that explains "how the internet works" in a few episodes.  There are transcripts if you don't want to listen to the author babble (and he does babble A BUNCH).  grc.com/sn .... then start with episode 25 (yes, it was long ago). Or a quick look at the [manpage for nsswitch.conf]("http://manpages.ubuntu.com/manpages/wily/man5/nsswitch.conf.5.html") might be sufficient to gain the understanding needed.  There is an order for name resolution on every networked computing device.  Each has some way, like the /etc/nsswitch.conf file to control it.  Usually, if you put anything into a /etc/hosts file, that will be found first and used. It is very effective at stopping internet tracking and ad networks too.  Just know that this is ONLY for the 1 PC where the changes exist.  Here's an article that I wrote a few years ago about that [https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)

Anyway, I suspect your hosts file is getting in the way or DNS isn't properly configured (the DNS for YOUR domain that you've registered), but without exact, accurate information, I can't look at that from here.  You can look at those settings with the 'dig' program.

---

### Post by tcmtrinity on 2016-09-13
> **TheFu said:**
> I hope not.  Only the required ports should be forwarded, not all of them. These words can have multiple meanings. Please clarify.

Used to run a TF server back in the early 2000s, just needed to get the correct ports for it to work.

From what I'm reading, it appears things are working as designed and just a little more understanding of networking, name resolution and DNS is needed on your part.  There is a podcast that explains "how the internet works" in a few episodes.  There are transcripts if you don't want to listen to the author babble (and he does babble A BUNCH).  grc.com/sn .... then start with episode 25 (yes, it was long ago). Or a quick look at the [manpage for nsswitch.conf]("http://manpages.ubuntu.com/manpages/wily/man5/nsswitch.conf.5.html") might be sufficient to gain the understanding needed.  There is an order for name resolution on every networked computing device.  Each has some way, like the /etc/nsswitch.conf file to control it.  Usually, if you put anything into a /etc/hosts file, that will be found first and used. It is very effective at stopping internet tracking and ad networks too.  Just know that this is ONLY for the 1 PC where the changes exist.  Here's an article that I wrote a few years ago about that [https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)

Anyway, I suspect your hosts file is getting in the way or DNS isn't properly configured (the DNS for YOUR domain that you've registered), but without exact, accurate information, I can't look at that from here.  You can look at those settings with the 'dig' program.

I should have said all relevant ports are forwarded. My bad.

Thing is everyone outside the house connects to my external IP and everything works. At the house if I only use internal IPs everything works. But as soon as I try to use a lan computer to connect to the linux server via my external IP it doesn't work.

The hosts file is my prime suspect. But I can't seem to crack that nut.

The only thing missing from my setup working perfectly (enough for me at least) would be to be able to connect to the linux server on my lan using my external IP.

---

### Post by bab1 on 2016-09-14
> **tcmtrinity said:**
> I should have said all relevant ports are forwarded. My bad.

Thing is everyone outside the house connects to my external IP and everything works. At the house if I only use internal IPs everything works. But as soon as I try to use a lan computer to connect to the linux server via my external IP it doesn't work.

The hosts file is my prime suspect. But I can't seem to crack that nut.

The only thing missing from my setup working perfectly (enough for me at least) would be to be able to connect to the linux server on my lan using my external IP.
The problem does not sound like a DNS problem.  Google "NAT Reflection".  In any event you are still connecting to the same host.

---

### Post by TheFu on 2016-09-14
If the /etc/hosts file has the name you want to use to connect to the WAN port with a 127.x.x.x, then that will never happen.

If you want to connect using external DNS resolution ... 
mysubdomain.mydomain.com needs to resolve to the WAN public interface. How you make that happen is up to you. Can be in the /etc/hosts or you can let mysubdomain.mydomain.com be resolved by external DNS.

---

