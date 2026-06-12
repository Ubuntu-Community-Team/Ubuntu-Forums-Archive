---
title: "Setting up SSH Tunnel from University network"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by skarecrowster on 2008-11-05
Hello there, i'm fairly new to Linux, and so far haven't reverted back to Windows for anything... I'm based at University throughout the week, but come home for weekends, trouble is, as with most .ac.uk establishments, they tend to block access to any sites that contain various keywords, which is pretty annoying as i cant get into a whole lot of popular sites...

Anyways, i'd like to know if its possible to somehow use an SSH Tunnel to my home broadband connection.... (not sure if this is the correct terminology)

I've looked into doing this but the terminology just baffles me, is there anyone out there who could explain this in a 'for dummies' kind of way...??? I'm pretty computer savvy (2nd yr Computer Forensics) but networking jargon confuses me no end...

The connection in my home is connected to broadband through a Netgear ADSL router, which is always left on, however, my home PC is only running XP ... The laptop i want to connect from, is running Xubuntu and has the FoxyProxy add-on

I realise this maybe a little too much to ask, but any help would be greatly appreciated ...

Thx ... Skare!

---

### Post by skarecrowster on 2008-11-05
by the way, i'm running 8.04

---

### Post by pmsumner on 2008-11-05
It's dead easy to do.  Assuming you can already SSH into your home PC, look at:

[http://jstrassburg.blogspot.com/2006/01/howto-tunneling-http-over-ssh-with-dd.html](http://jstrassburg.blogspot.com/2006/01/howto-tunneling-http-over-ssh-with-dd.html)

or

[http://ubuntu-tutorials.com/2008/06/18/tunnel-web-and-dns-traffic-over-ssh/](http://ubuntu-tutorials.com/2008/06/18/tunnel-web-and-dns-traffic-over-ssh/)

or

[https://help.ubuntu.com/community/SSHHowto#Breaking%20out%20of%20a%20controlled%20network](https://help.ubuntu.com/community/SSHHowto#Breaking%20out%20of%20a%20controlled%20network)

SSH has the functionality to allow port forwarding/redirection, so you tell your SSH client to forward all connections to 127.0.0.1:xxxx (xxx is any port number) to the server, which sends the requests from there instead and sends the replies through the SSH tunnel to your PC.

---

