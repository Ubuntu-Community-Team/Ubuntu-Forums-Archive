---
title: "My web site not found &amp; Firefox hangs. Any ideas?"
date: 2023-05-10
forum: Networking &amp; Wireless
---

### Post by managerrose on 2023-05-10
On Ubuntu 22.04 using nginx, curl rose-server.duckdns.org hangs, as does rose-server.duckdns.org in Firefox. nginx is shown as active(running) by sudo service nginx status nginx. I can ping rose-server.duckdns.org Ok.

/etc/nginx/sites-enabled/rose-server.duckdns.org has link to/etc/nginx/sites-available/rose-server.duckdns.org. 

certbot setup Ok for rose-server.duckdns.org.

[https://rose-server.duckdns.org](https://rose-server.duckdns.org) (in Terminal) gives:
manager@Desktop:/etc/nginx/sites-available$ wget [https://rose-server.duckdns.org](https://rose-server.duckdns.org)
--2023-05-10 19:23:21--  [https://rose-server.duckdns.org/](https://rose-server.duckdns.org/)
Resolving rose-server.duckdns.org (rose-server.duckdns.org)... 92.24.27.85
Connecting to rose-server.duckdns.org (rose-server.duckdns.org)|92.24.27.85|:443...

Ports 80 & 443 on router have port forwarding to same numbered ports on computer. Ports 80 & 443 are open on computer's firewall.

---

### Post by TheFu on 2023-05-11
I can reach it.  If you cannot from inside the LAN, then it is likely your router is set to prevent this.  It is a security thing.
The easiest solution would be to use something called a "split DNS."  Run an internal DNS that resolves any internal addresses correctly when you are inside the LAN and allow public, external, DNS to resolve addresses when outside.  You could also add the LAN IP address to any client-system /etc/hosts files inside your LAN.  This probably won't work for Android devices, however.  Google decided that using /etc/hosts was a security risk on Android, so only DNS seems to work (or it did when I needed it).  

I use a pi-hole install for my LAN DNS (among other things). It runs inside an LXC container on one of my servers.

---

### Post by managerrose on 2023-05-13
> **TheFu said:**
> I can reach it.  If you cannot from inside the LAN, then it is likely your router is set to prevent this.  It is a security thing.
The easiest solution would be to use something called a "split DNS."  Run an internal DNS that resolves any internal addresses correctly when you are inside the LAN and allow public, external, DNS to resolve addresses when outside.  You could also add the LAN IP address to any client-system /etc/hosts files inside your LAN.  This probably won't work for Android devices, however.  Google decided that using /etc/hosts was a security risk on Android, so only DNS seems to work (or it did when I needed it).  

I use a pi-hole install for my LAN DNS (among other things). It runs inside an LXC container on one of my servers.

Web site accessible Ok when away from home. As you say, either my cheapo router (TP-Link TD-W9970) is setup to prevent it. or could it be because I'm accessing the website on the same computer as I created it?

Could you point me to a web page giving instructions on how to setup an internal DNS?

---

### Post by TheFu on 2023-05-13
If a website will be public, don't run desktop applications on it.  That's Security 101.
How to setup a DNS is covered all over the place.  Do you really need me to google it for you?  I'd use "ubuntu 22.04 dns server" as my terms and look for results that have "ubuntu" in the domainname part, not just in the URL.  I'd favor help.ubuntu.com for the answer.

---

### Post by managerrose on 2023-05-14
> **TheFu said:**
> If a website will be public, don't run desktop applications on it.  That's Security 101.
How to setup a DNS is covered all over the place.  Do you really need me to google it for you?  I'd use "ubuntu 22.04 dns server" as my terms and look for results that have "ubuntu" in the domainname part, not just in the URL.  I'd favor help.ubuntu.com for the answer.

Since I only need access to my website when I'm testing any new html  & files on my web pages, I found that the simple static ip address  on my LAN allows me to do that.
Though my website is public, it's  purely a personal one (without any personal info on it) which is useful  when I want to access certain info away from home.
Why do you state "If a website will be public, don't run desktop applications on it."? In other words, why is it a security threat to have desktop apps on a computer running a website?

---

### Post by TheFu on 2023-05-14
[https://krebsonsecurity.com/](https://krebsonsecurity.com/) is one place to start.  I've been at this so long that it is intuitively obvious to me why allowing internet traffic into a desktop is a terrible idea.

---

