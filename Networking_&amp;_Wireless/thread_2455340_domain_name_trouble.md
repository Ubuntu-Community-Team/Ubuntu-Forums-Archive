---
title: "domain name trouble"
date: 2020-12-17
forum: Networking &amp; Wireless
---

### Post by mexenus on 2020-12-17
Hello hello,
I am completely new to this so maybe I am on the wrong part of the forum please tell me if so !
So my problem is that I passed on a random tutorial on how to make your very own web server there, well it looks super easy on that tutorial so being a little bit handy with computers i get myself a cheap second hand computer.

After a lot of fighting with that one I finally manage to get ubuntu server 20.04 working properly.Then came the problem thatthe server was only accesible from my own network so again, again a lot of frustration but later on i dscovered about public ip so that was the reason that couldn't just enter my computers ip to acces the server being on mobile data.
Then I learned about port forwarding so I setup my router so to forward port 80 the server and 22 as well. 

But now i am with the problem that I can't seem to "link" (I dont now if its the right word) my domain name to my server, I tried to enter everything that I could imagine on the configuartion panel from my domain name. I spend hours trying to find something on Google but no I can't seem to link them. I'm geting absolutely crazy !
I don't now what to do anymore !

Kind regards, and thanks in advance for any kind help ! For more info feel free to ask I would be pleased to get it for you !

---

### Post by TheFu on 2020-12-17
Many home ISPs block ports 20-23, 25, 80, 137-139, 443, 445, and a number of others to protect end-users from internet hacking. If your ISP blocks port 80/tcp inbound, then you cannot use that port for anything. No way around it except to change ISP plans (business accounts?) or change to an ISP that doesn't block.

In some countries, even the public internet address for their clients are "private" and non-routable.  This again is for security reasons.  It completely prevents all inbound connections.  I've seen this in China and India and on almost all cellular data connections.

An old article about what you need to host a website: [https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site)
My last bill with a registrar was for $19/yr.  Major racket.  A few weeks ago, I migrated from that $19/yr company to a different one for $7.  That gave me about 2 yrs to find a cheaper alternative.  If I could, I'd buy 20 yrs of registration for 1 domain and 2 yrs for my other 20 or so domains.

If you just want to run a private website, then you don't need any registrar, just a way to know what the current IP address is for your public WAN connection.  My article doesn't discuss that, but you can get a free sub-domain from a number of dynamic DNS providers. Some WAN routers have this option spelled out in the interface and will maintain the correct IP automatically.  I ran using dyndns for over a decade, but switched to having a static IP for my home business long ago, so my subnet on the internet doesn't change, ever.

For private servers, please don't use port 80 on the internet.  Setup ssh on a non-standard port and setup an ssh-socks-proxy so you can access any web servers on your home LAN securely over an encrypted ssh tunnel.  Don't use port 22 for ssh on the internet. That's a good way to be hacked.

My blog (see link above) has all sorts of articles about using ssh, proxies, running web servers, scaling, virtual machines, setting up servers in a consistent way, etc. Hopefully they are helpful.  I don't tend to put exact commands into my blog. I try to discuss the "why", assuming people can use google to find the exact commands for "how."  Plus "why" articles have a much longer useful life than exact commands which change from release to release, distro to distro.  Chasing the 14.04 --> 16.04 --> 18.04 --> 20.04 how-to articles always seemed foolish to me. Other people can do that, if they like.

---

