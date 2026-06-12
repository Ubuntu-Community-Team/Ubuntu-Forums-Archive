---
title: "About:Ubuntu Lamp Localhost &amp; IP Address"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by abujp1993 on 2011-02-27
Hello, I am new on ubuntu and I installed Lamp on Ubuntu And I can Access to the page "index.html" on var/www with Localhost but can not access with my IP address Any Idea how to fix this thing?
Excuse my English.:(

---

### Post by Ben Page on 2011-02-27
Are you behind a router? If so, you need to set up a virtual server on your router and enable remote access (every router is different, so look for instructions for your router on how to do this). Also, you may need to access your server from another internet connection, because most routers redirect you to your settings/status page if you are accessing it from the same internet connection. You can bypass this by using a proxy or VPN tunnel service.

---

### Post by abujp1993 on 2011-02-27
Mr.Ben,
Thank you for your Fast Reply I will try to configure my Router.:)

---

### Post by The Cog on 2011-02-27
I think apache installs only listening on localhost by default. You have to edit a configuration file and restart apache to get it to listen on all addresses. I don't have apache installed here, but I think the configuration is in /etc/default/apache. Change the listening address from 127.0.0.1 to 0.0.0.0. Then restart apache.

Once the server is listening for connections from other computers, you should be able to see the web pages from your local LAN. 

If your router is doing address translation and you want people on the internet to be able to see the server, then you will have to configure port forwarding in the router - configure it to pass TCP port 80 to the server. This configuration is specific to the type of router you are using. Also, you will probably not be able to connect to your public internet address from inside your LAN - you will have to use your private address from inside your own network.

---

### Post by abujp1993 on 2011-02-28
Thank youuu for your help i learn a lot but can't figure it out right now i can access it from my localhost & local ip address([http://192.168.xx.xx/](http://192.168.xx.xx/)) & now i want to access it by my freinds home (it's not working yet from my freinds home) what should i have to do? Once again I'm Truly Newbie ;)

---

### Post by kwacka on 2011-02-28
There's a good chance that you are connected to your ISP via DHCP rather than a static IP.

To get around this, check out [https://help.ubuntu.com/community/DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS")

---

### Post by Kulgan on 2011-02-28
[LIST]
[*]Go to your router's internal IP address (192.168.1.1 or something).
[*]Look for NAT (network address translation) **or** DMZ (demilitarised zone).
[*]DMZ: Set this to the internal IP of your web server. Beware that this forwards everything to your computer - potentially not very safe.
[*]NAT: You want to set up a forwarding rule that takes traffic from external TCP port 80 and forwards it to port 80 on the internal IP of your computer.
[/LIST]
And yes, your ISP using DHCP might be a problem. For myself, I've had the same "dynamic" IP for several months at a time.

---

### Post by abujp1993 on 2011-02-28
Thx for your fast reply ill try what you said!!

---

### Post by Ben Page on 2011-02-28
You should follow all instructions posted previously, but you should also check if your ISP enables server functionality for your subscription plan. There are ISPs that will block outgoing servers for home users with basic subscriptions. Since you use dynamic IP, this may be the case.

The main configuration file is usually called httpd.conf, and is located in /etc/httpd or /etc/apache2 folder.

The most important question is, what are you trying to do? You can accomplish different things in many different ways.

---

### Post by abujp1993 on 2011-02-28
> **Ben Page said:**
> You should follow all instructions posted previously, but you should also check if your ISP enables server functionality for your subscription plan. There are ISPs that will block outgoing servers for home users with basic subscriptions. Since you use dynamic IP, this may be the case.

The main configuration file is usually called httpd.conf, and is located in /etc/httpd or /etc/apache2 folder.


Mr.Ben
I'm trying to follow all instructions but i don't know how to follow (I don't have so much knowledge) but I searched a lot on all previously posted instructions for follow them but failed :(

& sure I will search for "ISP" bcuz I don't know about that too...

I found httpd.conf file on /etc/apache2 & i opened it It's empty


> **Ben Page said:**
> The most important question is, what are you trying to do? You can accomplish different things in many different ways.


I made a website thats locate on var/www i can see that on localhost but my friends can not see my website using my IP address.


> **Ben Page said:**
> Are you behind a router? If so, you need to set up a virtual server on your router and enable remote access (every router is different, so look for instructions for your router on how to do this). 
Yeah, I have 2 routers i bought one for wifi othere one is from Internet Company
I dont know the mean of Virtual server (You mean, do i have to open port 80?)


Thx agggaaainnnnn.:):

Excuse my english.

---

### Post by The Cog on 2011-03-01
By having a virtual server, he means you must configure your router to forward incoming connections to the web server. Without that configuration in the router, it won't know what internal IP address to forward incoming connections to. 

A web server listens on TCP port 80, so this is the port that you need to forward. So assuming your web server is something like 192.168.1.69, then you need to se the router up with something like:
**TCP 80 -> 192.168.1.69 80**
but how this is done is different in each make of router. If you can tell us the make of router, mayne someone will be able to post better instructions.

---

### Post by abujp1993 on 2011-03-02
Thank you :) I Called to SupportCenter & they tell me the way to port forward (80).

Ihave a problem When i see (What is my ip) on web & put it to web browser its not working Which ip do i have to give to my freinds to access my server?

& im not sure but i don't have a static IP.

---

### Post by The Cog on 2011-03-02
You need to give your friend your public IP. Fir testing, you can visit [http://www.whatismyip.com/](http://www.whatismyip.com/) and tell him that address. If you don't have a static IP address, then that will change from time to time, so you probably want to read up about dyndns where you can register your current address with a public name server.

---

### Post by abujp1993 on 2011-03-02
It wooooooorkkssssss you people helped me alot:)

Special Thanks to::KS:KS:KS! Mr.Ben Page & Mr.The Cog !:KS:KS:KS

Thxxxx

---

