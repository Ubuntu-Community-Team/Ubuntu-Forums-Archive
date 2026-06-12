---
title: "[SOLVED] Accessing my server inside and outside my LAN with a unique address."
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by mat087 on 2008-03-10
Hi,

My server is in my LAN located at 192.168.1.2. To access my server within the LAN, it's 192.168.1.2. However, when I'm outside my LAN, to access my server it's [my_public_ip].


Is there a way to access my server with a unique address that will work when I'm inside and outside my LAN ?


Thanks,
Mathieu

---

### Post by Eiríkr on 2008-03-10
Look into something called "port forwarding".  Basically it's a way to tell your router that anything coming in from outside on port XXXX should be forwarded to port YYYY (possibly the same port number) on internal address ZZZ.ZZZ.ZZZ.ZZZ.  Then you'll just have to remember whatever you set XXXX to, and append that to the IP address when accessing from outside.  So say you've got a web server running on the default port 80 for within your LAN.  From inside, you'd just type the server's hostname or IP address: [font=courier]http://192.168.1.2[/font].  To set it up for external access, you'd configure your router to forward port 8080 on your external IP address to port 80 on your internal IP server address of 192.168.1.2.  So from outside you'd type [font=courier]http://EXT.IP.ADD.RES:8080[/font] to access the same web server.

HTH,

Eiríkr

PS -- If you don't have a static IP address for the outside world (if you've got a consumer-grade ISP connection, you don't), your IP address is "dynamic" and will probably change every so often.  To give yourself a static, unchanging presence in the outer world, look into signing on with a [dynamic DNS service provider]("http://www.google.com/search?q=dynamic+dns"), which provides DNS (i.e. internet naming) services for people with dynamic IP addresses.

---

### Post by mat087 on 2008-03-10
Basically, I'm running a SSH server on 192.168.1.2:22. On my router I've set to forward port 9999 to 192.168.1.2 : 22.

I've got a dynamic IP, so I use dyndns.org.

When I'm outside my LAN, i can `ssh xxx.dyndns.org -p 9999`. However, when I'm inside my LAN `ssh xxx.dyndns.org -p 9999` doesn't work. I need to `ssh 192.168.1.2`. I would like that `ssh xxx.dyndns.org -p 9999` works when I'm inside and outside my LAN.


Mathieu

---

### Post by Eiríkr on 2008-03-10
Aha, that's a bit different than what I understood from your initial explanation.  I just duplicated your setup on my end, and ssh works for me using the external IP + port, after setting up port forwarding on the router.  This begins to sound like it might possibly be a firewall or other setting issue on your router.  Or, possibly, for some reason the closest DNS cache to you has the wrong IP address associated with your dyndns.org hostname.  Find out what your current external IP address is, and try connecting to that and see if that works instead.  If it does, it's a DNS cache issue.  Reducing your DynDNS TTL setting might possibly help, especially if it's a large number.

Sorry I can't be of much more help here, but good luck.

Cheers,

Eiríkr

---

### Post by lloyd_b on 2008-03-10
> **mat087 said:**
> Basically, I'm running a SSH server on 192.168.1.2:22. On my router I've set to forward port 9999 to 192.168.1.2 : 22.

I've got a dynamic IP, so I use dyndns.org.

When I'm outside my LAN, i can `ssh xxx.dyndns.org -p 9999`. However, when I'm inside my LAN `ssh xxx.dyndns.org -p 9999` doesn't work. I need to `ssh 192.168.1.2`. I would like that `ssh xxx.dyndns.org -p 9999` works when I'm inside and outside my LAN.


Mathieu

What nameserver do you use when you're inside your LAN?  Do you have any control over it?  If so, then all you need to do is define "xxx.dyndns.org" to point to 192.168.1.2.

Other than that, the only way I can think of would be to have a script that determines whether you're inside or outside of your LAN (maybe by your IP address) and switches between two versions of the file "/etc/hosts" - one with a definition for "xxx.dyndns.org" and one without.

Lloyd B.

---

### Post by jetsam on 2008-03-10
Some routers don't support this at all: they won't let you access internal servers by the external ip.

Some routers do support it, but you have to enable a setting.  Look for "Filter Internet Nat Redirection" in your router administration page or documentation.  

My own router supports it but doesn't seem to allow me to turn it off even if I wanted to.

Maybe a workaround if your router doesn't support it is to put the dyndns address in your hosts file mapped to the correct local ip address.

---

### Post by mat087 on 2008-03-10
Thanks for the reply guys.

My nameserver is "192.168.1.1". (By the way I'm running "DD-WRT v23 SP2 (09/15/06) micro" on my router.)

The idea to detect on my laptop if I'm inside or outside my LAN seems to be a good workaround. I'll check this solution :)

Thanks,
Mathieu


P.S There is something strange... If I type my xx.dyndns.org in my browser when I'm inside my LAN I can access to the setting of my router (which is at 192.168.2.1:80). (Note : port 80 is not forwarded).

---

### Post by Eiríkr on 2008-03-10
If you can indeed access your router that way even when not accessing from within your LAN, that sounds like a potential security concern -- anyone could try to brute-force your router's admin password.  I'm not familiar with DD-WRT, but my default D-Link router interface includes an option for access to the admin pages from external addresses -- which I have turned off.  I suspect DD-WRT might include something similar?  

Meanwhile, it's also possible that DD-WRT is doing something cute like treating requests for the router's external IP that originate from within the LAN as if they were aimed at the router's internal IP, which I saw on another old D-Link router I had.  Access to the external IP worked from within the LAN, but not from elsewhere.

---

### Post by mat087 on 2008-03-10
> **Eiríkr said:**
> If you can indeed access your router that way even when not accessing from within your LAN, that sounds like a potential security concern -- anyone could try to brute-force your router's admin password.  I'm not familiar with DD-WRT, but my default D-Link router interface includes an option for access to the admin pages from external addresses -- which I have turned off.  I suspect DD-WRT might include something similar?  


This is just working when I'm inside my LAN.

And "Remote access" is disabled.


Mathieu

---

### Post by Eiríkr on 2008-03-10
Okay, whew, then it's just the router being cute, and no need to worry about external brute-force takeover attempts.  :)

Cheers,

Eiríkr

---

### Post by jetsam on 2008-03-11
I'm not familiar with the DD-WRT, either, but it seems from a few google searches that I've done that it should support NAT redirection.   Look for the "Filter Internet NAT redirection" setting, possible under security.  I believe it should be deselected to enable the functionality you want.  

That may fix your problem without resorting to scripting.  Or, maybe not.  I'm not sure I understand what's going on with you being redirected to the administration page from inside the network.

---

### Post by mat087 on 2008-03-21
I finally found the option for my problem, it was "loopback".

Thanks to everyone.

Mathieu

---

### Post by Eiríkr on 2008-03-21
Glad to hear you found a solution!  :D  If you're all set then, please also remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  

Thank you,

Eiríkr

---

