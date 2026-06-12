---
title: "Network down, every day at the same time"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Kev0r on 2007-11-08
Hello,

I'm on Gutsy, the server edition, just did a fresh install.
Installed dhcp3-server, and shorewall.

The server is connected to internet configured with dhcp.

It also acts as a router for local computers in the network.

But every day, at about 7-7:30 PM my network connections go down.
Doing a sudo /etc/init.d/networking restart on the server will instantly fix my problems. (Till the next day)
But local (not dhcp, but static to 192.168.0.1) will go down also. And my internet connection (dhcp) is down too.

Does this ring a bell with anyone?

---

### Post by SpiritIsReality on 2007-11-08
howdy
I'm just a beginner at this, but I think it sounds like a cron job? Set to run at 
around 7-7:30 PM every day.
I'd have to man cron and google a few places to figure out how that goes again.
I read a bit of it about a month ago. I've been reading a few different books trying to find out just which one to study. So I can't remember which one it was.
I could be way off on my guess too. 
trails

---

### Post by Kev0r on 2007-11-08
Hi, a cron job would be verry strange.
I'm the only one with access to that box and i've not put it there :)

---

### Post by timcredible on 2007-11-08
see if your ethernet connection dropped (dmesg).  if so, maybe someone is running something each night on the switch that drops your connection.

you said you're not using dhcp?  is there dhcp on the network?  if so, could be that another machine is getting your address via dhcp, which would make the switch change it's mac address table and effectively disconnect you from the network.

---

### Post by Kev0r on 2007-11-08
That would not explain the local downage though. I've changed nothing on the setup, just removed Ubuntu 6.06 and installed 7.10 (clean)

Wow, syslog went CRAZY around that time, feel like it's some mallicious.

check this out: [http://hulsteijn.net/networkdown](http://hulsteijn.net/networkdown) (plain text file)

---

### Post by SpiritIsReality on 2007-11-08
howdy
I don't have any answers. I just tried to trim some of the fat without missing anything important.
attachment. 
edit: rats, it didn't upload.
it's a .tgz 4136 bytes.
I'll try a gz or a tar, I guess tgz isn't on the list.
The trimmed text file I made is 40 KB , max allow 20 KB.
trails

---

### Post by SpiritIsReality on 2007-11-08
hope it works this time. It's a 50KB tar and the limit is [IMG]http://ubuntuforums.org/images/uf/attach/tar.gif[/IMG] **tar** 	976.6 KB

---

### Post by AndyCanty on 2007-11-09
Hi, i've just starting playing with Ubuntu, but your problem sounds like the DHCP lease.

Sounds like your switch is restarting, i have a silmiliar problem on my gutsy server ,ip resets and reverts to DHCP eve though it's set to static.
i know my swicth is ok other wise i wold have major problems.

so if anyoine has any other ideas I would be most grateful.

Hope that helps.

Andy.

---

### Post by kvonb on 2007-11-11
-

---

### Post by jeffjohn on 2007-11-11
This might sound really stupid, but....in my household where a Cat5 runs 10m through the loft, outage occurred when eco. flourescent bulbs were stitched on! Changing my ADSL filters to 'active' ones cured the problem.  My ADSL link is 5km to exchange and s/n quite poor. Max speeds 800mbs. All perfectly stable now; I had exhausted all computer/router borne possibilities.  jeffjohn

---

