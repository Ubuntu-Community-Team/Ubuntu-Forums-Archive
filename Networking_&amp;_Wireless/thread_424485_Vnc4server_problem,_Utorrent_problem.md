---
title: "Vnc4server problem, Utorrent problem"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by lo-fi on 2007-04-26
Hello guys, I have some problems administering remotely a dedicated server. This is the problem :
I'm connecting via Putty to the server and log in without problems. Now I'm trying to install vnc4server so I can administer remotely from my desktop via VNC Viewer. I followed the instructions from a &#919;&#927;W-TO thread that I found here, but still can't connect. I installed vnc4server and xinetd, I set the password (vncpasswd /root/.vncpasswd) for vnc, and typed vnc4server :1, to start the vncserver, but it gives me this error 

> 
xauth: (stdin):1:  bad display name "xxxx.yyyyyyy.zzz:1" in "add" command

New 'xxxx.yyyyyy.zzz:1 (root)' desktop is xxxx.yyyyyy.zzz:1

Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/xxxx.yyyyyy.zzz:1.log

where xxxx.yyyyyy.zzz = the domain/ip of the server

So I'm trying to connect from my desktop with the vnc viewer and it says that connection refused..


I have another problem also, before this problem come up, I was connecting via Vnc to the server without a problem, but I was having another problem too. I installed wine, and downloaded utorrent. So I set up utorrent, I'm doing the test to see if the port that I have chosen is port forwarded and it shows me that's is open. So all ok until this step. I add some torrents to seed, but I can't connect to noone (peers I mean), it doesn't even shows me the number of seeders and leechers (it shows 0(0) and 0(0) ), also in the tracker status it shows that tracker is offline, but I tried with several trackers and still it doesn't connect to any peer, it doesn't download anything...
I don't know what to do, the port is forwaded, I don't know where's the problem. It might be the firewall that blocks connections? I even tried to configure iptables but nothing happenned. I did several restarts but still nothing happenned.
My os is Ubuntu Desktop 6.0.6. Please guys some help, I don't have enough experience with linux to cope with these problems..
Any suggestions???

---

