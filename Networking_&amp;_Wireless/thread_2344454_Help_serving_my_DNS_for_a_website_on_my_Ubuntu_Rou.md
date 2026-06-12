---
title: "Help serving my DNS for a website on my Ubuntu Router"
date: 2016-11-25
forum: Networking &amp; Wireless
---

### Post by bwanger on 2016-11-25
Hi Everyone,

 Im looking for some help on going about this properly, I setup my own home router using the ARS site ([http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](http://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/)) and was wondering the best way to get the box to host the DNS for domain I purchased?  I wanted to host it on another ubuntu server I can run apache on, so essentially setup DNS to point to this internal IP of a host running apache/my website at home on my home internet service. Kinda new to this so if you can point me the right direction to get my hands dirty it would be great.  Thanks!

---

### Post by ian-weisser on 2016-11-25
You are simply hosting the IP address (the *domain*) that the *domain name* refers to.
The DNS vendor that is renting you the domain name will take care of the DNS. You simply need to tell them your router's IP address.

Advice: This device will be connected 24/7 to the dirty, dirty internet. Within the first hours, it must withstand thousands of attempts (brute-force and clever) to compromise it. Start by thinking GOOD SECURITY HABITS.

Advice: Learn how to build a router using a VM before you start on hardware.

Advice: Learn how to build a server using a different VM before you start on hardware.

Advice: Learn how to use a container once you are familiar with VMs. Containers have much less overhead.

Advice: Put the webserver in a container, so that a server crash (they happen) doesn't kill your network. Network-down makes it very hard to research how to fix your server!

---

### Post by bwanger on 2016-11-29
Thanks for the advice! I went the hardware route using the ARS article for the main reason I wanted a secure router. I have it set to do automatic updates which should add to the security of it being exposed to the internet. I currently have an ESX server specifcally for testing but chose using standalone hardware for performance (I have a "gigabit") connection. 

In relation to pointing to my router, since the ISP is giving out a dynamic IP I would need a way to resolve this, I had it configured through my router using the Zoneedit service but not sure how I can go about getting functioning properly on my router box and running Bind. Any input?

---

### Post by ian-weisser on 2016-11-29
Use a DDNS provider for a dynamic IP address. That's all they do.
Usually, your server hosts a tiny 'heartbeat' client that helps to adjust the DDNS record when the IP address changes

---

### Post by kpatz on 2016-11-29
Zoneedit provides DDNS service.  I have a custom script that updates my DNS record when my IP changes, but I think there are ddns packages for ubuntu that will do it.  Looks like ddclient is a good one from my limited googling, and it appears to support Zoneedit.

---

### Post by 1clue on 2016-11-29
Forgive me if I'm mistaken in the impression that you haven't exposed a Linux box to the outside world before.

You really want this thing locked down before you expose it directly. I advise looking at these links to start:
[LIST=1]
[*][https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[*][https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[*][https://www.ubuntu.com/usn/](https://www.ubuntu.com/usn/)
[*][https://nvd.nist.gov/](https://nvd.nist.gov/)
[/LIST]

I'd follow that up with google searches (not necessarily Ubuntu-specific but not excluding Ubuntu either) to for best practices for all software that will be used on the box, and then all software installed on the box.

When I do this I start by installing the specific apps I need and remove everything else I know I can remove. If you don't have an app then its vulnerabilities (known and unknown) don't hurt you.

I would also suggest that you read up on and understand how bugs/vulnerabilities are found, reported, fixed and pushed to end users.  Not only from the standpoint of the good guys but what happens when the bad guys find a vulnerability. Understanding this will help you when your system has been hacked.  Keep in mind that there is a significant time between the discovery of a vulnerability and the installation of the fix on your system. Also keep in mind that the fixes only change the software, they do not mitigate damage done if your system was compromised before you installed the patch.

I would seriously avoid putting any sensitive information on this server until you get your head around the issues here.

Good luck and have fun.

---

### Post by 1clue on 2016-11-29
Another thing. A small office/home router is notoriously insecure. If you put critical data at this site at all, you'd be well served to get high quality hardware and software. This specifically includes removing all consumer-grade security appliances and wireless routers.

IMO you should have a separate network for any wifi access which can't reach your public servers on any maintenance port (http yes, ssh no) and prevent access to everything except your intended-to-be-public from the outside altogether. Security-wise, a network with wifi access is a public network.

---

