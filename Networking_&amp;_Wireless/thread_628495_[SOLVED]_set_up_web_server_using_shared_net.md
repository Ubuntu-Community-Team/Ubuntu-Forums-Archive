---
title: "[SOLVED] set up web server using shared net?"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by lian1238 on 2007-12-01
Hi,

I would like to set up a home web server using apache. But, I'm connected to the net through a host computer running windows xp. I am running Ubuntu Gutsy. The connection between the two is a direct LAN cable. The host computer uses a USB ADSL modem. What do I need to do so that my web server can be accessed outside this network of two?

Any help or tips would be much appreciated. Thanks.

---

### Post by victorbrca on 2007-12-01
You have to forward port 80 (HTTP) through your ICS.

I found this screenshot that may help ya...

[IMG]http://www.dslreports.com/r0/download/181339;bd105dc7c26c9fbad8be83372f13319d/icsconfigXP.jpg[/IMG]


Vic.

---

### Post by lian1238 on 2007-12-02
Thanks for the screenshots, Vic.
I will try that after I get everything installed on this Ubuntu machine.

But, what IP address would my web server use? The IP address on my host? (e.g the IP I get from whatismyip.com) Then, if I want to use DynDns to link to my server, I would have to install the Updater on the host computer, right?

---

### Post by victorbrca on 2007-12-02
No problem!! :)

If the server will be installed on your Linux box, it will use it's own IP, which is the internal. The updater can be installed on either machines (eg: if you visit what's my IP.com on each machine, both will get the same result).

Imagine like this:

WAN IP = 98.98.98.1
XP IP = 98.98.98.1 (as long as your modem is on transparent mode. Check the IP result from what's my IP.com against "ipconfig" on a XP terminal)
Tux = 192.168.1.1

So the server IP will be 98.98.98.1:80, which is equal to 192.168.1.1 (because of the 80, which is the protocol. This is done automatically, so on dyndns will be 98.98.98.1, but everytime someone tries to connect on 98.98.98.1 via port 80, the XP box will forward that request to your tux box)

Hope I ddn't confuse you!!!  :-S

Vic.

---

### Post by lian1238 on 2007-12-02
Oh, thanks for the info!

I noticed that my IP, as shown on whatismyip.com, is the same as the host's. And when I switched to Linux, I couldn't install the USB modem on it. So, I let my XP be the host. But then, I couldn't access my site from outside.

Alright then, I'll start by install the necessary software on my Linux server. :D

I'm still not sure how I'll test if other people can visit my site.. unless I ask my friends (nicely) to try. Hehe.

I'm off being a web admin!:D

---

### Post by lian1238 on 2007-12-03
I've installed apache now and I can access the /var/www/ directory by going to localhost. I've set a static IP address on my LAN to 192.168.0.2 whereas the XP host is 192.168.0.1. I've gone into the ICS settings on the host and checked the Web Server (HTTP) service and set the IP address to that of my Linux box.

But, I still have a problem. When I go the the IP address of my host on the internet (i.e. the IP from whatismyip.com), I get the "Unable to connect" page. I don't know what's wrong. I've also open port 80 on the host computer, and used Lokkit to configure my Linux box too. I can access the server from the host computer by going to 192.168.0.2, though.

Help, please?

---

### Post by victorbrca on 2007-12-03
You can't access your internal server by using your WAN IP (external). I don't remember the reason but you can't. You have to try from a machine from another location.

Now, if you want to you can redirect requests to your domain to your internal address. Lets say you use your server to host pictures. One day you post one of those pics in a forum. When you open the post you'll not be able to see the pics because the link for the pic is pointing to your own WAN address, so this are two options you have:

1- Change hosts file on Windows and Linux:
- Windows
mydomain.dyndns.org        192.168.0.2
- Linux
mydomain.dyndns.org        127.0.0.1

2- Add Route
-Windows
<WAN IP> <WAN Mask> 192.168.0.2
- Linux
<WAN IP> <WAN Mask> 127.0.0.1



Vic.

---

### Post by lian1238 on 2007-12-05
I've asked a friend of mine, outside my network, to access my server using the WAN IP, and YES it worked! I haven't got the chance to play around with the hosts file on the Windows host but I've tried it on my Linux. In /etc/hosts I added this:
```
http://www.yahoo.com 127.0.0.1
```
but, I still get to Yahoo instead of the server. I've also tried this after a restart.
Is there a problem with my Linux hosts file?

---

### Post by victorbrca on 2007-12-05
> **lian1238 said:**
> I've asked a friend of mine, outside my network, to access my server using the WAN IP, and YES it worked! I haven't got the chance to play around with the hosts file on the Windows host but I've tried it on my Linux. In /etc/hosts I added this:
```
http://www.yahoo.com 127.0.0.1
```
but, I still get to Yahoo instead of the server. I've also tried this after a restart.
Is there a problem with my Linux hosts file?

I used to do this with no problem on my Windows machine, but I could never get it to work on my Linux box. I even posted on a thread in regards to this. 

To make it work I changed it on my firewall, which is a BSD box.

Try adding a route on the Windows box and it should apply to both...

Vic.

---

### Post by lian1238 on 2007-12-05
Thanks Vic.

I noticed you use dyndns.org, too. Are you hosting your site on your home computer?

---

### Post by victorbrca on 2007-12-05
No problem.... 

I have a very old server at home which is where my ftp and web server are...

[IMG]http://wazem.dyndns.org/temp/my-network/CIMG4542%20(Small).JPG[/IMG]

[IMG]http://wazem.dyndns.org/temp/my-network/CIMG4541%20(Small).JPG[/IMG]


Vic.

---

### Post by lian1238 on 2007-12-15
Wooow, very cool! :)
I have an old computer too. Except, it's sitting inside a box. :lolflag:

---

### Post by victorbrca on 2007-12-16
lol...  ;)

---

