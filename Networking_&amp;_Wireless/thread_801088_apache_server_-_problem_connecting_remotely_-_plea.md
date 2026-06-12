---
title: "apache server - problem connecting remotely - please help!"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by jacksmash on 2008-05-20
I've spent hours on this now... I'm really not sure what I'm doing wrong.

First of all, I've setup an apache web server, and it seems to be installed correctly because I can access my webpages from /var/www/ from any computer on the network. However, I wish to be able to connect from an outside computer - but so far I've had no luck.

I'm behind a Linksys BEFW11S4 router - which I know is old, but that's what I'm working with. I've tried forwarding other ports besides 80 for http, because I realize some ISP's block 80 for incoming traffic (I am calling them now to verify this).

Is there some configuration I have to do on my end to get this to work? I've even tried SSH with no success. (but all of this works from computers on my network).

Any help or suggestions would be greatly appreciated!

---

### Post by jacksmash on 2008-05-20
Have I posted this in the correct forum? Perhaps I should have it in the servers one - although I didn't install the server version of ubuntu.

---

### Post by SpaceTeddy on 2008-05-20
first off, you are in the right forum. 

Apache2 will (by default) answer any request made to it via any name. That means it will respond to any dns name and to any ip-address that connects to it. 

Since you say you can access your server from the local machines, i would put my money on a port forwarding problem with your BEFW11S4. Make sure you are forwarding port 80 to the correct IP address, and when accessing the server from the internet you must use the IP if the router - NOT the one from the server that runs the apache2. 

that is about all i can think of that is wrong... really

---

### Post by jacksmash on 2008-05-20
Thanks SpaceTeddy. I have a feeling it's a port-forwarding or port-blocking problem as well. The IP of the machine I'm running the server on is 192.168.1.103, and so in my router settings, I add "HTTPD 80 80 ... 192.186.1.103". (Actually, I can only add the "103" portion of the IP because the router has the other numbers blacked in - for good reason).

The IP of the router itself (from [http://whatismyipaddress.com/](http://whatismyipaddress.com/)) is XX.XXX.XXX.XXX, and that's the address I type into a browser from another computer. I know there's a message on my answering machine from my ISP back home - so I'll check it out later tonight. My feeling is that they've got ports blocked for incoming traffic. That is unless, of course, I've set up my router incorrectly.

Does everything look right from what I've just explained?

Cheers.

---

### Post by jacksmash on 2008-05-20
Well, I just found out that my ISP blocks all ports - so I'm going to have to find some workaround I suppose.

---

