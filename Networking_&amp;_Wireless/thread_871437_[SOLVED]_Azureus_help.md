---
title: "[SOLVED] Azureus help"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by janthes on 2008-07-26
Hi all.

I'm having a problem with Azureus. When I launch Azureus in Kubuntu, I get an error something to the effect that port 50138 is firewalled. When I'm in XP, I don't get that error, it shows that I'm accessible. I checked my router's UPnP configuration, and it says that Azureus configured port 50138 and everything is groovy.

This is a recent event. I've torrented in the past with Azureus in Kubuntu with no issue. Does anyone know a fix?

Thanks.

---

### Post by warchief_ryan on 2008-07-27
You'll need to open the port, im guessing your using iptables, I like to edit the rules with UFW, which you have to enable first,

enable it
"sudo ufw enable"

deny stance recommended for security reasons
"sudo ufw default deny"

then allow the port, it will allow from everyone
"sudo ufw allow 50138"

then test it with Azureus, should be open.


I'm assume you didn't add any other firewall.

---

### Post by janthes on 2008-07-27
Thanks for the reply warchief_ryan!


I updated ufw precisely to your instructions, but I still get:


"Error UPnP: mapping "Incoming Peer Data Port (UDP/50138 )' failed"

Any other pointers?

---

### Post by Diabolis on 2008-07-27
You might me behind a firewall, setted outside of your computer. IP tables won't help here.

For example my ISP gave me an access point, so I can access the internet through it with my laptop. The access point comes with its own security settings, so it must be blocking the ports that you need.

You either open those ports or tell Azureus to use another range of ports.

More about port forwarding: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by janthes on 2008-07-27
Thanks for the quick reply, Diabolis.

As I've said in my first post, I'm fully reachable in XP with Azureus using port 50138.

I know that my ISP doesn't throttles or blocks torrents. I don't think it's any thing dealing with linux either. I just used KTorrent and everything seems swimmingly on the download side (I prefer Azureus over KTorrent though).

Anymore suggestions? 

Thanks.

---

### Post by Diabolis on 2008-07-27
Yeah google around with the error message.

[http://www.google.com/search?hl=en&q=mapping+Incoming+Peer+Data+Port+UDP+50138+failed&btnG=Search](http://www.google.com/search?hl=en&q=mapping+Incoming+Peer+Data+Port+UDP+50138+failed&btnG=Search)

Seems like this thread explains it:

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/601332.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/601332.html)

---

### Post by janthes on 2008-07-27
YAY!!! I got it to work (apparently). I'm shown as connected now. Thanks for the help and links Diabolis!

---

### Post by Diabolis on 2008-07-27
I'm glad. If it keeps working well, don't forget to mark the thread as solved.

---

