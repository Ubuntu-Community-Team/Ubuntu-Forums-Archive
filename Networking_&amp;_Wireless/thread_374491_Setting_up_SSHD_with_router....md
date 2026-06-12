---
title: "Setting up SSHD with router..."
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by fcoster on 2007-03-02
I'm a recent ubuntu convert, running Dapper happily. 

My dapper box is connected to my DSL connection with a wireless PCI card, through a Linksys wireless router. I would like to be able to SSH into my dapper box from my laptop.

I've downloaded and installed OPEN-sshd, and I think its running fine on the dapper box. If I "ssh localhost" at the terminal, I can log in with no problems. I know that I need to forward port 22 from the router to the dapper box, and I think I've done that. When I ifconfig on the dapper box, it lists the "inet addr" as 192.168.1.102 and Bcast as 192.168.1.255. (What's the difference between these two IPs?) I've put the first of these IPs in the router's port-forwarding menu. I've attached relevant screenshots, showing the router's setup.

Then, I get my IP from whatismyip.com, and try "ssh [ip from whatismyip.com]" but I just get 
> ssh: connect to host ---.---.---.--- port 22: Connection refused

What am I missing? Is the fact that the dapper box is connected to the router wirelessly an issue? (I assumed not.) I think its possible to set up the dapper box to receive a static ip from the router... but is it necessary for this to work? (And if it is necessary, how is it done?)

Thanks very much,

Chris

---

### Post by chili555 on 2007-03-02
Maybe it is we who are missing something. Are you trying to get to 192.168.1.102 from the outside world? Your office or school? Or are you trying to get to it from another room, like when I ssh into my wife's machine downstairs and make it play flatulence sounds. If it's from the outside, I hope some others more experienced will hop in to help.

If you are trying to ssh to it from inside your LAN, simply ssh -l user 192.168.1.102.

A static IP is a practical necessity. You can easily set it under System -> Administration -> Networking. Put the IP address you currently have, Netmask 255.255.255.0 and Gateway 192.168.x.x (whatever the IP address is of your router, I'd guess 192.168.1.1). Close and you will be all good.

---

### Post by fcoster on 2007-03-02
chili555 - Thanks!

I feel a bit stupid that was so simple. I used the locally assigned IP and all was well in the world... excellent. I can now get at files in my computer upstairs, from downstairs...

If I wanted to ssh in from the outside world, could I just use the IP I get when I visit whatismyip.com from the dapper box? (I know it is dynamically assigned by my IP, but it is the same for at least a couple days at a time.. so if I need to SSH in from school, that should work, right?)

Thanks again.

---

### Post by nyinge on 2007-03-02
Yes, but I would recommend using a port other than 22, since port 22 is a well known port for ssh, and you'll be getting hundreds of break-in attempts literally every day.  I'd choose somewhere between 20000 and 65000.  I'd also recommend changing the password every quite often.

---

### Post by Zelut on 2007-03-03
Two suggestions here:

1) you can use a free dynamic DNS service such as dyndns.org which will help you access your local machines remotely.  i have that setup (my router supports it) so I can use a myname.dyndns.org and not need to worry about a changing IP.

2) I wrote a few tips on securing ssh on my blog and the comments include quite a few more.  Having ssh access to your home network is very nice, but its also a neccesity to lock it down.  See what I put together here:
[http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/](http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/)

---

