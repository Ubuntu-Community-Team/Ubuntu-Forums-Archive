---
title: "HTTP connection times out from local wireless network.  (Can telnet from outside.)"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by damakable on 2008-11-22
I'm hosting a simple web interface to a couple search engines for a course I'm taking.  Everything's up and running on localhost and through 192.168.x.x, but trying to connect through my public IP from my PC or other computers in the network times out.  This is through Apache2 and a 2Wire router, courtesy of Bell.  I've temporarily disabled the firewall, though I've never had problems with Firestarter.

I can ping my public IP from my own PC, but not from others in the network.  I can't telnet into port 80 from elsewhere on the network either.

Interestingly enough, I can telnet into my site from an SSH connection to a computer at school, and I can even use Lynx to connect to my site and use the search engines, even though I can't ping the IP (and I'm not filtering ICMP packets, either).  What I'm wondering is whether I can reasonably assume that my site will work in the browser when I go to the lab on Monday to show it working, and why it is that other computers on the network and the machine running the server can't connect through telnet, lynx, or a browser.

At this point it's not mission-critical, and I can always install this running locally in the lab, but I'm curious as to how to get everything running smoothly at home, accessible from anywhere.

Any suggestions?  What commands should I run and post the results of?  Here, maybe part of my Apache config will help.  It's just plain html and cgi...

<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        </Directory>

        <Directory /home/*/public_html/cgi-bin>
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                AddHandler cgi-script .cgi
                Order allow,deny
                Allow from all
        </Directory>
</IfModule>

---

