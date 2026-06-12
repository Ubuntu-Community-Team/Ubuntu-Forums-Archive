---
title: "Can the same email and web domain point to different servers?"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by Twizzle on 2008-11-19
I am relatively new to this but have set up a home server that runs Ubuntu 8.04 and serves files and backups. I am in the process of adding a groupware type application such as Citadel to manage email, contacts and calendar.

I own a domain and have an email account using that domain with 1and1. The plan was to be able to have my server download the emails from the 1and1 server using pop3 and then store them for access around the home and on my mobile. I have almost got all of this working internally at home.

Once it is up and running I want to open my router to the world so I can access the server from anywhere. I have a Dynamic IP address but have tried DynDns and it seems to work ok.

What I would like to know, though, is if it is possible to use my domain and have it point at my server for web access but still use the same domain for email into the 1and1 server.

Eg [www.thisdomain.com](www.thisdomain.com) would go to my server but [email]me@thisdomain.com[/email] would go to the 1and1 server.

I hope that makes sense…

---

### Post by SpaceTeddy on 2008-11-19
in theory, yes, this can be done. Normal lookups for domain go towards the A record of a nameserver, while mail goes towards the mx record. if no mx exists, then it is send towards the A record. 

So, in other words, they can be different. BUT - this will not work for you, as your home server does not have a static ip (why else whould you use dyndns ?) - and you cannot update the 1&1 fast enough to keep track of where your home server is. Of course, if you have a static ip at home - it's in the control center somewhere - all you have to do is point the A towards your ip, and the the mx towards the 1&1 mail server.

cheers

---

### Post by Twizzle on 2008-11-19
Thankyou for that and it does all make sense now.

My ISP is Virgin and I know that they use dynamic IP's but understand that they do not change very often. Plus I leave my router on 24/7 (and I assume that *holds* onto the IP? ).

I guess I could update 1&1 with that IP and change it on the occassion that my IP address changes. I know that I could run the risk of not being able to log in one day but (if the set up goes to plan) my mobile will still sync and the email will still be recieved correctly into the 1&1 server?

I will give it a try and see how I get on.

As for DynDns, I thought that they offered a service where I could point my domain, through them, to a dynamic IP. Does any one know if that means I would have to lose my 1&1 email account?

---

### Post by superprash2003 on 2008-11-19
well even though your router is on 24/7 .. it need not hold onto the ip.. there is a Lease time, after which the ip changes.. typically its once in 24 hours..and if your ip changes and for it to update on your domain it could take approx 24- 48 hours.. so its not something easy to do with a static ip..what you could try is noip plus service.. [www.no-ip.com](www.no-ip.com)

---

