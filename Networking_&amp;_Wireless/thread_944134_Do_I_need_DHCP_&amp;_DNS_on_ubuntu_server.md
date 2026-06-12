---
title: "Do I need DHCP &amp; DNS on ubuntu server"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by rmkapil on 2008-10-11
I have just installed ubuntu 8.04 Desktop at my home.  I will use it as a web server and also a desktop for development.  I also need to install openSSh so that I can connect to it remotely from my office network.

Please let me know if I also need to install DHCP and DNS.
I do not have a static IP.
Thanks,
rmkapil

---

### Post by blastus on 2008-10-12
If you don't have a static IP address then you'll have to know what it is before you can use it from the Internet. Some people post their IP address to the Internet and then they visit a web page to find out what it is. Since you don't have a static IP address chances are your ISP has a policy against hosting with your account.

I would probably get a router. Using a router is just easier and later on if you get a second machine and/or upgrade/reinstall Ubuntu, you can just plug it into the router. A good router is WRT310N and you can put DD-WRT on it for all the functionality you could possibly need.

---

### Post by Iowan on 2008-10-13
DHCP & DNS would only be useful if you have other clients on the network - even then, (as mentioned) the router could probably handle it. I took DHCP off my router and had an internal server handle it - mostly to let my '486-based (Freesco) router concentrate on being a router/firewall.

---

