---
title: "Strange internet problem"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Cellular on 2007-03-24
Hi, i have a really strange problem. I can't access the internet through my university network (Uppsala University, sweden) on my laptop (hp nx7400) with Ubuntu.

Let me explain: i have a broadband connection through my university, and to access the internet i first have to log in through a portal page at the universitys server. I can access this page an log in, and i can access other pages at the same server, but i can't access any other websites. 

I'm running the Feisty beta, but the same problem appeared under Edgy and even when i boot the Edgy Live Cd. The strange thing is that i am running Edgy on my stationary computer, and that can use the same internet connection without problems. I also have no problems when running my WinXP-partition on the same laptop that is having the problem.

I get ping reply from the login server, but no other server (i have tried a few google ip-numbers), so it's not a DNS-problem, nor a firefox problem. I've tried disabling the firewall through Firestarter, and that doesn't help either.

I've had no problems using other broadband connections with this laptop and Edgy.

To summarize: the problem appears when i use the laptop, Ubuntu and the universitys broadband connection, but if i remove any one of the three everything works. 

The login page claims to be using Netlogon-117, whatever that means.

Please help, i'm going nuts over this! ](*,)

---

### Post by insane_alien on 2007-03-24
its a proxy configuration problem. i had the same problem at my uni(i didn't realise because my laptop came preconfigured for it, i bought it through the university)

anyway, somewhere on the portal site there should be a link that will take you to the proxy configuration you need. it'll probably be a file named 'proxy.config' or something.config

in firefox go into the preference then advanced/network/settings and it should give you an option to use an automatic configuration script from an URL. put the URL in then go log in through the portal. worked for me.

if you can't find a proxy configuration on the login site then you can just go ask someone at the IT helpdesk for the proxy configuration and you can put it in manually

---

### Post by Cellular on 2007-03-24
Thanks for the pointer, although i tried a couple of proxy configurations and didn't get it to work. I also haven't configured any of my other systems to use the proxy. I'll look into it some more though, and if i can't get it working i'll call the university it support.

---

### Post by insane_alien on 2007-03-25
yeah, you might have to restart the wireless card after you change the proxy settings. i  had to do that with mine.

---

### Post by Cellular on 2007-03-26
I've solved the problem now, so i'm posting this for future reference, in the very unlikely event that someone else should have the same problem.

As it turns out, when i log on through Ubuntu i recieve another ip address than when i log on through windows, actually another ip address than i should recieve, and this ip address was blocked by the university because someone had used it and had a virus on their computer. IT support unblocked the ip, and now everything works.

What are the odds?

---

