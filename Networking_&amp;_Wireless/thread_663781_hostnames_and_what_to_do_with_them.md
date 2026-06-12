---
title: "hostnames and what to do with them?"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by TorchlightJay on 2008-01-10
Hey all. 

I have a server in my office that I gave a hostname. It's just a one word hostname and for example, we'll call it EXAMPLE. Now I am nots ure how I am supposed to do it, perhaps I already have things in order. But I want to setup a network using LDAP and setup a firewall and currently this server hosts 5 websites, soon it'll host 7 under apache2. 

Can I have multiple hostnames on one server. Whenever I do uname -n or hostname it says EXAMPLE. When I try to setup stuff under mysql, I set it up as localhost. When I am setting up wordpress I'd like to set them up for each website with the websites hostname rather that just hostname. And then Of course I am going to setup a network with a domain (thought I don't have a dns, i just use godaddy) and have it bee example.mydomain.net or whatever.

I guess what my main question is, in terms of networking, since I have more than one domain being used for my systems, is it necessary or a good idea to have my server utilize more than just one hostname. If so, how do I do it? Thank you.

---

### Post by LeAstrale on 2008-01-10
as fas as i know you would need to do virtualization on your server to make machines with different hostname on 1 server.

---

### Post by TorchlightJay on 2008-01-10
I see, well I guess a question that will help me is what is the benefit of a hostname?

---

### Post by GavinZac on 2008-01-10
> **TorchlightJay said:**
> I see, well I guess a question that will help me is what is the benefit of a hostname?
hostname refers to the name of the host that the server is on; i.e., the physical or virtual machine.

it sounds like you want to give each website/user its own hostname, for that you'll need to set up virtual machines, or just leave it alone. I don't see that it is that important!

---

### Post by TorchlightJay on 2008-01-10
So essentially, as far as websites, apache, mysql and php are concerned, localhost or whatever hostname this box has is just fine? If so, then I worried about nothing.

Just to get a little off topic, I have a domain name hosted through godaddy and want to make my hostname reflect that (ie Example.mydomain.net) Am I able to do that as long as I have it reflected on the domain records in godaddy or do I need another server like DynDNS or make my own DNS server. What changes would I have to make on my current one? 

Thanks

---

### Post by GavinZac on 2008-01-10
> **TorchlightJay said:**
> So essentially, as far as websites, apache, mysql and php are concerned, localhost or whatever hostname this box has is just fine? If so, then I worried about nothing.localhost is a catch-all :) it will always go to the application's local host, without needing to specify the exact name. most likely, that isnt actually the hostname of your box.

---

### Post by TorchlightJay on 2008-01-10
Oh i know it's not my hostname, but I do use it alot cause it's pretty much like a default name. I just wanted to make sure that it was safe to use, like if I can use it in lieu of my actual hostname and yield similar results.

---

### Post by GavinZac on 2008-01-10
> **TorchlightJay said:**
> Oh i know it's not my hostname, but I do use it alot cause it's pretty much like a default name. I just wanted to make sure that it was safe to use, like if I can use it in lieu of my actual hostname and yield similar results.

Sorry, I read it wrong. Yes, its safe :)

---

