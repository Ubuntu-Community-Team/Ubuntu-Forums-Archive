---
title: "L.A.M.P question"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by chemicalgr on 2007-07-15
Hello there I'm using Ubuntu feisty I'd already installed a LAMP server before,now i want to test if this works via internet.
What is the address which someone types to "view" my files in the var/www folder?
What type of address is required how can i know if my ip is static or dynamic?
A! do not forget to mention that before the installation of my modem (sagem 840) I used to type 127.0.0.1 to view my files of my "demo" server and everything was ok,now after the installation it doesn't work,what's going on?
Sorry for my bad English
Thanks for your patience.**[B]**[/B]

---

### Post by Mr. C. on 2007-07-15
chemicalgr,

The first thing you need to determine is your own external IP address.  It may be static, or dynamic, but that isn't very important right now.  You can discover your own IP at this site:

[http://whatsmyip.org/](http://whatsmyip.org/)

Once you have that, other's can reach you via that IP address:

[http://your.ip.address](http://your.ip.address)

This will get packets to you - now its up to your server to do something with those requests.

If you have a firewall, you need to allow incoming port 80 TCP traffic, forwarded to your web server's LAN address.

Your web server needs to be configured to respond to those requests, and server the pages you desire seen.  There are several types of configuration, but lets take small steps until you become more familiar with the process.

After this, you can setup name-based hosting, where others will reach your different sites, based upon the host name they use to reach you.

MrC

---

### Post by chemicalgr on 2007-07-15
Thanks MrC

---

