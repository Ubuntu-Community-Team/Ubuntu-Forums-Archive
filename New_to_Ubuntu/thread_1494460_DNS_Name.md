---
title: "DNS Name?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Whisp3r on 2010-05-26
Hi all. Thank you all for your help earlier with SSH.

I would like to register my IP address with a name, so instead of typing out of my IP address, I can just drop in a URL. Aside from getting a fixed IP from my ISP, do I need to do anything else? Or do I just get the name from a registrar and point the name at the IP my provider gives me? 

This is my first time doing this. Looking forward to learning. Thanks! :)

---

### Post by -humanaut- on 2010-05-27
If your using a router you can setup a static IP through it. I think thats what your asking?

---

### Post by Whisp3r on 2010-05-27
> **-humanaut- said:**
> If your using a router you can setup a static IP through it. I think thats what your asking?

No, I mean if I wanted to buy the domain [www.mywebsite.com](www.mywebsite.com) from somewhere like GoDaddy and register my IP address to it for the purpose of connecting to my SSH server or what have you, do I need to do anything else other then obtain a static IP?

---

### Post by Ozymandias_117 on 2010-05-27
I think what you're looking for is this: [http://www.dyndns.com/services/dns/dyndns/]("http://www.dyndns.com/services/dns/dyndns/") Also, that should allow you to do what you want without paying your ISP extra for a static IP

---

### Post by CharlesA on 2010-05-27
Use a dynamic DNS service such as dyndns.com.

---

### Post by Whisp3r on 2010-05-27
Thank you. I don't need to get permission from my ISP or anything to point a Dynamic DNS at the IP? Thanks. :)

---

### Post by CharlesA on 2010-05-27
No, you don't need to get permission from yer ISP to do that. You usually need to run a program on the server or router that updates the IP address if it changes.

I've got mine set up thru my router.

---

### Post by Whisp3r on 2010-05-27
Thank you. This is all new to me, so I appreciate all the help. :) What program would you recommend that updates the IP address? I'm off to register my first domain name! :)

---

### Post by TheUnwiseman on 2010-05-27
Just make sure your ISP allows you to run a server out of your home.

---

### Post by iMisspell on 2010-05-27
> **TheUnwiseman said:**
> Just make sure your ISP allows you to run a server out of your home.
I would not do this, they might charge you extra.
In the past (about 6-7 years ago) they tried to charge me extra while just talking to them about it (this was from a phone company with DSL), i told them forget and when off and ran a web server (IIS under windows 2000) anyway and i never heard a word from them. 
I would just do what ever you plan on doing, and if they say anything, just play dumb, and say you didn't know.

_

---

### Post by Whisp3r on 2010-05-27
> **iMisspell said:**
> I would not do this, they might charge you extra.
In the past (about 6-7 years ago) they tried to charge me extra while just talking to them about it (this was from a phone company with DSL), i told them forget and when off and ran a web server (IIS under windows 2000) anyway and i never heard a word from them. 
I would just do what ever you plan on doing, and if they say anything, just play dumb, and say you didn't know.

_

True that. I don't have any plans to run anything more then a SSH tunnel to browse securely, and be able to access my files on my home computer from afar.

---

### Post by TheUnwiseman on 2010-05-27
> **iMisspell said:**
> I would just do what ever you plan on doing, and if they say anything, just play dumb, and say you didn't know.

Ignorance of your ISP's ToS (Terms of Service) is not an excuse for breaking them.  You can be charged some hefty fines for running a publicly available server out of your house.  iMisspell is partially right in that most people get away with doing this anyway.  But I would still be careful.

---

### Post by CharlesA on 2010-05-27
> **Whisp3r said:**
> Thank you. This is all new to me, so I appreciate all the help. :) What program would you recommend that updates the IP address? I'm off to register my first domain name! :)

I was using ddclient (it's in the repos), before pushing that job off to my router.

> **TheUnwiseman said:**
> Ignorance of your ISP's ToS (Terms of Service) is not an excuse for breaking them.  You can be charged some hefty fines for running a publicly available server out of your house.  iMisspell is partially right in that most people get away with doing this anyway.  But I would still be careful.

That's probably true. The ISP usually just blocks the ports of commonly used servers and leaves it at that.

The only server I have "publicly" available is SSH.

---

