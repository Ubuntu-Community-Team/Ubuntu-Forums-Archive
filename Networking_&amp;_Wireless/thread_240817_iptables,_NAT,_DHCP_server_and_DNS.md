---
title: "iptables, NAT, DHCP server and DNS"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by harisund on 2006-08-21
ok, so here's my current setup

Internet(ISP)--Cable modem--router WAN Port

                            router LAN port--computers

In place of the router, I want to place my Linux box. So here's my new setup

Internet(ISP)--Cable modem--Linux eth0
                            Linux eth1--switch--computers

This is at my house, and I want it transparent to my room mates. Right now, their computers' (all Windows) are configured for DHCP and they get their addresses nicely from the router and have no idea about anything else. I am guessing I can setup a DHCP server on my Linux box, crossover it to a switch and my room mates won't know the difference, right? 

That, and of course, I need my Linux box to do NAT as well. It has to share the ethernet connection on eth0 from the ISP, just like my router does. 

Once I accomplish that, I want my Linux box to act as sort of a DNS server, maintaining the names of all of my friend's machines so that we can use that easily while gaming, file transfer and stuff. 

Oh and of course, port forwarding as well. I want to forward a few ports, like those for web servers, ssh server and some torrents as well.

And finally, I want my DHCP server to hand out the same IP address (through DHCP) to machines based on MAC numbers. This way, I know I can port forward 80 to 192.168.0.67 (for example) and ensure that 192.168.0.67 is always handed out to my webserver box.

Possible? Anybody ready to guide me through it? 

Thanks!

---

### Post by Iowan on 2006-08-21
Should be possible.  I'll see if I can find a couple of how-to's.

[Here's one]("http://www.ubuntuforums.org/showthread.php?t=111972"), [Another one]("http://howtoforge.com/perfect_setup_ubuntu_6.06")

---

### Post by harisund on 2006-08-21
Thanks Iowan. 

Could you tell me how you are searching for them? I would like to do some searching myself too, if only I could get the correct search terms :)

---

### Post by ohgod on 2006-08-21
I have a setup like this at home.  Sadly, it's on a Slackware box so my config won't help you too much (I haven't converted it yet...).

This guide looks ok (it uses a program called Webmin to simplify setting up the various servers):[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html")

---

### Post by harisund on 2006-08-21
I don't mind really. I would be grateful if you could just let me know what you did on your Slackware box. I am familiar with Linux in general, and am sure I can adapt it to any other Linux box. 

Thanks a ton !

Hari

---

