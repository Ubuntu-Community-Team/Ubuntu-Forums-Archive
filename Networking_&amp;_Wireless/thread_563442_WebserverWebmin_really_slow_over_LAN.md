---
title: "Webserver/Webmin really slow over LAN?"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by william_hunter on 2007-09-30
I can't seem to figure out how to make my webserver (upstairs in my house!) and webmin communicate nicely with computers via LAN. It is stupendously slow to access both of these things, and also my PHPBB2 forum, but outside of my house things are all hunky-dory. Should I look into using Bind to provide DNS service or something?

---

### Post by william_hunter on 2007-09-30
Oh, and I have already edited the hosts file of each computer I use on the LAN. The webserver/webmin works really quite well when I am on the server itself, logging on through localhost.

---

### Post by william_hunter on 2007-10-12
Update: I can now access Webmin from afar, but my forum just won't work properly. Does anyone have insights about why this might be? Nobody on the phpBB2 boards seems willing to tackle this one either. I took down the hardware firewall and am just relying on iptables now, forwarding ports for the things i need, and Webmin seems to be ok, as does the game server i host, but for some reason the forum isnt.

---

