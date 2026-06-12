---
title: "How to setup Web hosting server."
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by shoaibnawaz on 2007-11-03
A fibre optic internet connection is installed in my office. A server is set up using Windows 2003 Server for web hosting. I want to know that how can I replace it Ubuntu server. I can install Apache, PHP and MySQL on it. What are the additional set up required to configure regarding DNS.

---

### Post by Soarer on 2007-11-03
As you probably know, you can set-up Ubuntu server including the LAMP stack using the Server CD.

I don't know that you'll need to set-up DNS for a web server, only for a file or print server (and maybe not then, I get IP addresses from my router).

Your web server will (likely) get a fixed IP address from wherever the other end of the fibre optic goes. You need to ensure that the Internet's DNS servers point the url you are using to that IP address (contact whoever is parking your domain for you currently).

Then, traffic from the Internet will be directed to your server and Apache will do the rest, once you have uploaded your web site to it.

If this is not what you meant, please let us know.

EDIT: Sorry, I reread your post. If the Windows server is getting it IP address from the ISP providing the optic, it should work on Ubuntu (using the DNS client which is installed by default). If not, you will need to manually tell the DNS client which IP address to use.

---

