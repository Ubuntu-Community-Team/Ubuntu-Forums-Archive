---
title: "Slow Transmission Bit Torrent Client"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by ProNux on 2008-11-16
Guys, I am on dual boot (Ubuntu Hardy and WinXP).  I am planning to remove the Windows XP soon, only that, I still use uTorrent @ XP to download torrents.

I find the Transmission Client @ Ubuntu very slow.  Is there a way how to configure it?  I have been searching for similar threads but can't find one.

Thanks...

---

### Post by ProNux on 2008-11-16
Guys, I found a thread regarding OPENING of a port.  I learned that Ubuntu, by default, does not accept incoming ports and so you have to open it manually.  Thanks.....

Here's the post for those with similar problems.  Thanks to Choad.

[http://ubuntuforums.org/showthread.php?t=331161&highlight=transmission](http://ubuntuforums.org/showthread.php?t=331161&highlight=transmission)

---

### Post by markg48 on 2008-11-16
its partly the settings and the seeders some seeders put min downloading so u get slow speed from them like 1 kb second

---

### Post by ProNux on 2008-12-12
> **markg48 said:**
> its partly the settings and the seeders some seeders put min downloading so u get slow speed from them like 1 kb second

Got your point bro, but when I open the same torrent at Windows (utorrent client), it was faster.  Now, My Transmission client is as fast as in Windows's utorrent.

---

### Post by dk21 on 2009-01-06
Try to run in console:

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

and

sudo iptables -A INPUT -p udp --dport 6881 -j ACCEPT

(change the port number...)


and then, incrase the maximum peers in preferences...

I was downloading slowly because I couldn't handle more peers... I incrased it to 200 and I got a great speed incrase: 40 to 450Kbps ;)

in the torrent you can see "downloading from X of Y connected peers". In my case, 50 was the maximum...

PS: Got almost 600kbps...

---

### Post by ProNux on 2009-01-21
> **dk21 said:**
> Try to run in console:

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

and

sudo iptables -A INPUT -p udp --dport 6881 -j ACCEPT

(change the port number...)


and then, incrase the maximum peers in preferences...

I was downloading slowly because I couldn't handle more peers... I incrased it to 200 and I got a great speed incrase: 40 to 450Kbps ;)

in the torrent you can see "downloading from X of Y connected peers". In my case, 50 was the maximum...

PS: Got almost 600kbps...

Thanks for this one. Almost exactly same procedure I found on the other thread...

---

### Post by jfluet on 2009-01-24
and then, incrase the maximum peers in preferences...

I was downloading slowly because I couldn't handle more peers... I incrased it to 200 and I got a great speed incrase: 40 to 450Kbps ;)

were do i do this???

---

### Post by rrbarbosa on 2009-01-29
Hey everyone,

I also this problem with speed on Transmission. Here I have a dual boot with XP, and there with bittorrent client things are much faster.

I tried the changes on the iptables and raising the number of maximum peers (200 total and 200 per torrents) but I still see no speed improvements. The only thing I see different is that I do not use the same port number, as I share internet (i am behind a NAT, but i have port forwarding), I just pick a random big number (26476) to use. Does the port number change anything?
Any other advise?

By the way, on Transmission Preferences->Peers, the app says that the port is Open.

Thanks

---

### Post by ProNux on 2009-02-01
> **rrbarbosa said:**
> Hey everyone,

I also this problem with speed on Transmission. Here I have a dual boot with XP, and there with bittorrent client things are much faster.

I tried the changes on the iptables and raising the number of maximum peers (200 total and 200 per torrents) but I still see no speed improvements. The only thing I see different is that I do not use the same port number, as I share internet (i am behind a NAT, but i have port forwarding), I just pick a random big number (26476) to use. Does the port number change anything?
Any other advise?

By the way, on Transmission Preferences->Peers, the app says that the port is Open.

Thanks

It might be that the torrent you are downloading has very few seeders, since your port is open.  Just an idea...

---

### Post by aalian on 2009-02-17
> **dk21 said:**
> Try to run in console:

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

and

sudo iptables -A INPUT -p udp --dport 6881 -j ACCEPT

(change the port number...)


and then, incrase the maximum peers in preferences...

I was downloading slowly because I couldn't handle more peers... I incrased it to 200 and I got a great speed incrase: 40 to 450Kbps ;)

in the torrent you can see "downloading from X of Y connected peers". In my case, 50 was the maximum...

PS: Got almost 600kbps...
hey

thanks for taking the time.

I did what u said; the result was a decrease from 50 to 30 peers, although i entered the port number mentioned.

any comments ?

thanks again

---

### Post by o0Chris0o on 2009-03-27
Hey guys, I am having this same problem, I tested me speed online and I have great download speed!

I have port 6881 open on Transmission also tried "sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT" I still get slow speeds with high seeded torrents. On windows I always got really good speeds.

Thanks for the help in advance.

---

### Post by sumandega on 2009-03-28
Hello all

I am new to linux but I have been doing some readings from here and there. I have noticed that the speed measurement in ubuntu is KB/s while in windows it is Kb/Sec. i think this makes the difference. but i would love to someone confirming it for me :)

---

### Post by tanusgreystar on 2009-04-02
> **dk21 said:**
> Try to run in console:

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

and

sudo iptables -A INPUT -p udp --dport 6881 -j ACCEPT

(change the port number...)


and then, incrase the maximum peers in preferences...

I was downloading slowly because I couldn't handle more peers... I incrased it to 200 and I got a great speed incrase: 40 to 450Kbps ;)

in the torrent you can see "downloading from X of Y connected peers". In my case, 50 was the maximum...

PS: Got almost 600kbps...


I typed the above commands, but Bit Torrent still says port 6881 is closed. I'm also very new to Linux.

---

### Post by tanusgreystar on 2009-04-04
> **tanusgreystar said:**
> I typed the above commands, but Bit Torrent still says port 6881 is closed. I'm also very new to Linux.

I figured it out. I had to open the port for Bit Torrent :guitar:in Firestarter too!

---

### Post by a.toraby on 2010-08-30
I have installed transmission, deluge and utorrent in my ubuntu. But utorrent's download speed is very faster than two other torrent clients. for example transmission download a torrent with 50KBs but utorrent downloads that torrent with 150KBs!!!
when I load .torrent file in transmission it finds 2 seeders but utorrent finds 26 seeders and connect to 12 peers!

---

