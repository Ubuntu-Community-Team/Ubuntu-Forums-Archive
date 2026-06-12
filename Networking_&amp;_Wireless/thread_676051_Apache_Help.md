---
title: "Apache Help"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by dethredic on 2008-01-23
Ok, port 80 is not blocked by my ISP. I am not running a firewall. I have a WRT54G.

Now, I fooled around with Apache on windows about a year ago, and I was successfully able to get my server up and running. There were no problems. Back then I didn't have tomato (different router firmware).

Now, I am making a Linux server, to host one of my websites. And after spending a couple hours googleing and doing trial and error settings on my router, I still can't get it. I know know my server is working because I can access it via localhost.

So, here are some of the things I have tried:

[IMG]http://img167.imageshack.us/img167/747/90331355ho4.png[/IMG]
[IMG]http://img145.imageshack.us/img145/9523/56582969su0.png[/IMG]
[IMG]http://img145.imageshack.us/img145/4721/92037682ls5.png[/IMG]

I have tried various variations of these settings. Some times they were on or off while others were on / off.

Ok, I can access the server on another computer inside my LAN, using it's local IP (192.168.x.xxx). But not via my external IP 24.57.xxx.xxx

I have not yet had the chance to plug my comp directly into my modem, but if you can see something that I should change, or if there are other settings I need to change, that would be great! This is really frustrating me.

---

### Post by dethredic on 2008-01-23
Ok, I was able to plug my modem directly into my server and here are my results.

When I was directly hooked up to my router I did an Ifconfig.

my local IP changed from 192.168.1.137 to 24.57.208.24. I would have expected it to change to my external IP of 24.57.233.201. I then checked my external IP and it changed to 24.57.208.24. I re did the connection to check this was accurate, and it is.

Now, when directly connected to the modem my friend could type in 24.57.208.24 and he could see my site. So, the problem is 100% in my router. I will try to forward port 24.57.208.24

So, if I am hooked up directly to the modem my server works, and my IP changes. I need the router, or I won't have other internet... So, I am going to go back to the default Linksys firmware and see what I can do with that.

---

### Post by murmel on 2008-01-23
Check out: [portforwarding.com](http://portforward.com/english/applications/port_forwarding/Apache/Apacheindex.htm)! =)
You could always update your firmware [here](http://www.polarcloud.com/tomato).
[Here](http://www.polarcloud.com/tomatofaq#how_do_i_use_the_port_forwardi) is the official FAQ. Try it out =)

---

### Post by dethredic on 2008-01-23
Did you look at the picture?

I have forwarded port 80.

---

### Post by dethredic on 2008-01-23
Ok, I switched back to the default firmware, changed some settings, and now it works!

Weird.

---

