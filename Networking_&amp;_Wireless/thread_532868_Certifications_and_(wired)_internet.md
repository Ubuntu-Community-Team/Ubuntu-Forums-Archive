---
title: "Certifications and (wired) internet"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by Grafster on 2007-08-23
[Sorry if this isn't technical; don't know anything about networking or the proper terminology.]
I'm running Ubuntu (7.04) on a Acer TravelMate 230.
All Travelmate connections are **wired**.

Originally I connected through a linksys WRG54 router to my internet provider. Cable modem. My wife also connects through her Mac and hasn't had any problems.
I didn't either originally.

However my school has it's own network with some sort of "certificate" system. Initially to get a connection you have to open your web browser, it redirects you to a page, Firefox prompts you to accept a certificate, log-in with your student id and you're good to go.
After that (except when you're periodically prompted) you don't need to log on to the schools network; automatic internet connection.

_The problem_
The laptop (Travelmate 230) can't seem to maintain a network connection to home network. It frequently drops the connection. This never happened before. Since the other computers are all working on the home network fine I'm assuming that the school certificate is somehow related (the problem started to show up around the same time).

Unfortunately I don't understand where this "certificate" lives in Ubuntu, how to diagnose the problem or even what the problem is properly called.
Any explanations/suggestions/advice (ideally so I can have access to both the networks) would be greatly appreciated.

---

### Post by gashcrumb on 2007-08-23
So is it that the laptop works fine when you bring it to school and plug it into their network but then when you bring it home you keep losing connectivity on your home network?  I'm confused by the description...

The certificate you get prompted for by firefox is because they're using HTTPs and probably a self-signed certificate, i.e. one that's not signed by one of the standard root CAs (like Verisign or Thawte).  So firefox will prompt you if you want to accept the certificate.  You may be able to see it if you open firefox and go into "Edit"/"Options..." then click on "Advanced" and then "View Certificates", though I think firefox doesn't actually store this certificate, it's just verifying (and asking you) if the server's certificate can be trusted.

---

### Post by Grafster on 2007-08-23
> **gashcrumb said:**
> So is it that the laptop works fine when you bring it to school and plug it into their network but then when you bring it home you keep losing connectivity on your home network?  I'm confused by the description...
That's exactly it. Sorry if I was confusing.

> **gashcrumb said:**
> 
  You may be able to see it if you open firefox and go into "Edit"/"Options..." then click on "Advanced" and then "View Certificates", though I think firefox doesn't actually store this certificate, it's just verifying (and asking you) if the server's certificate can be trusted.
There is something there under web sites with the school name (but that may be their web java system for class class materials, homework, etc.).
Will try removing it and seeing if that works.

I assume that the big list of Authorities stuff is not to be touched?
(I have no idea what any of it is for...)

Thanks this was very helpful! (at least in terms of getting me started)

---

### Post by gashcrumb on 2007-08-23
You probably don't want to mess around too much with those certificates, especially the trusted root CAs, as you want to probably be able to access your bank site and other https-enabled sites properly. :-)

Okay, so the laptop works okay at school and is flaky at home.  

You're probably using a dynamic IP address, and the DHCP server of your linksys router.  What you want to do is when you plug your laptop in at home go to "System"/"Administration" and select "System Log".  Click on "daemon.log" in the left panel.  This is where the DHCP client logs any information as it aquires and renews DHCP leases with your DHCP server, either at school or at home.  Other programs log in this file as well, so you'll want to filter it by hitting ctrl-f and then type in "dhclient".  When at home, can you see any errors?

One other simple thing you can try is to unplug the power on the router for about 30 seconds or so and then plug it back in.  The services on these linksys routers tend to just die for no reason, I've run into problems with it myself, eventually I wound up replacing the router when it completely died on me.  I now have a netgear which so far has been a bit more stable...

---

### Post by Grafster on 2007-08-24
> **gashcrumb said:**
> 
One other simple thing you can try is to unplug the power on the router for about 30 seconds or so and then plug it back in.  The services on these linksys routers tend to just die for no reason, I've run into problems with it myself, eventually I wound up replacing the router when it completely died on me.  I now have a netgear which so far has been a bit more stable...
I've been down this route but a) this is my second replacement router and has behaved extremely well (robustly even) b)other computers connected to the network work fine c)I've repeatedly plugged it in and out but it doesn't have much of an effect, the network connection usually dies (for that computer only) within a few minutes)
  
> **gashcrumb said:**
> 
You're probably using a dynamic IP address, and the DHCP server of your linksys router.   When at home, can you see any errors?
This was exactly what I was looking for! Thanks for showing me how to find it.

I can see errors. But for some reason I can't copy/paste the errors (it picks up other data in the clipboard).Typed out a representative sample below. Sorry if there are translation errors, I did my best.
> There is already a pid file /var/run/dhclient.eth0.pid with pid 4753
> killed old client process, removed PID file
> DHCPRELEASE on eth0 to 255.255.255.255 port 67 interval 8
> DHCPOFFER from 192.168.1.1
> DHCPREQUEST on eth0 to 255.255.255.255 port 67
> DHCPACK from 192.168.1.1
20:46:39 > bound to 192.168.1.101 -- renewal in 32451 seconds
20:48:06 > There is already a pid file /var/run/dhclient.eth0.pid with pid 4753
20:48:06 > killed old client process, removed PID file
20:48:06 > DHCPRELEASE on eth0 to 192.168.1.1 port 67 
20:51:24 > There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
20:51:27 > DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
20:51:33 > DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
20:51:34 > DHCPOFFER from 192.168.1.1
20:51:34 > DHCPREQUEST on eth0 to 255.255.255.255 port 67
20:51:34 > DHCPACK from 192.168.1.1
20:51:34 > bound to 192.168.1.101 -- renewal in 35414 seconds
21:02:01 > There is already a pid file /var/run/dhclient.eth0.pid with pid 6150

These "there is already a pid file" errors followed by resets roughly match my experience in terms of losing internet connectivity.

School looks like
> There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
> DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
> DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
> DHCPOFFER from 10.1.32.3
> DHCPREQUEST on eth0 to 255.255.255.255 port 67
> DHCPNAK from 10.1.32.3
> DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
> DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
> DHCPOFFER from 10.1.32.3
> DHCPREQUEST on eth0 to 255.255.255.255 port 67
> DHCPNAK from 10.1.32.3
> DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
> DHCPOFFER from 10.1.32.3
> DHCPREQUEST on eth0 to 255.255.255.255 port 67
> DHCPNAK from 10.1.32.2
> DHCPNAK from 10.1.32.3
> DHCDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
> DHCPOFFER from 10.1.32.3
> DHCPREQUEST on eth0 to 255.255.255.255 port 67
> DHCPNAK from 10.1.32.3
> bound to 10.1.32.37 -- renewal in 261452 seconds

It keeps doing that for a while ...
(but there is only one PID file message at the beginning)

Thanks again for your help.

---

### Post by Roswellgrey on 2007-08-24
I don't want to chip in and spoil the flow of help here, but .... there is an oddity with your logs.

You know you said that you had to type in the logs ?  :)

It is possible that there is a typo here ?

20:51:34 > DHCPACK from 192.168.1.1
20:51:34 > bound to 192.168.1.1 -- renewal in 35414 seconds

Because that is not very healthy ( if its right ) 

EDIT  : Its implying that the Laptop has been given ( by DHCP) the exact same IP address as the Router itself.
That would be very bad .....

---

### Post by Grafster on 2007-08-24
> **Roswellgrey said:**
> It is possible that there is a typo here ?

20:51:34 > DHCPACK from 192.168.1.1
20:51:34 > bound to 192.168.1.1 -- renewal in 35414 seconds

I just looked at the log again. It's 192.168.1.101

Specifically
Aug 22 20:51:34 gtop dhclient :  bound to 192.168.1.101 -- renewal in 35414 seconds

Thanks for the catch. Will edit the original.

---

### Post by Grafster on 2007-08-29
nobody has any idea about the .pid message huh?

---

### Post by gashcrumb on 2007-08-29
Maybe it's network manager acting up on you, happens on my laptop from time to time, though in my case it's probably a wifi problem.  You could try manually setting a static IP address for your laptop via System/Administration/Network to see if you have decent connectivity.  You'll need to set your IP address to somthing between 192.168.1.2 and 192.168.1.99 so that it doesn't conflict with your router's DHCP pool.  You'll also probably need to take a look at what DNS servers your router is using from your ISP (should be on the "Status" page, you'll need these IP address when setting up your static IP.

If that works and you seem to have decent connectivity for a period of time you could try disabling NetworkManager (I think you just right-click on the NetworkManager applet and uncheck the "Enable networking" menu item).  You'll then need to go back into System/Administration/Network and set your network card (eth0, should have mentioned that before) so that the system aquires an IP address from DHCP.

Hopefully with NetworkManager disabled you won't "lose" your IP address and have to re-aquire it from the router all the time.

---

### Post by Grafster on 2007-08-31
Just thought I'd update that it actually it may be that I was using a bad ethernet cord.

I haven't had the time to really test but using a different (less destroyed) cord seems to be resolving the problem.

Apologies for the while goose chase and the lost time. Will update again when I'm sure.

---

### Post by gashcrumb on 2007-09-02
Yeah, that would do it too...  :-)

---

### Post by Grafster on 2007-09-16
It was the cord for sure.
I am an idiot.
Thanks again for the help!

---

