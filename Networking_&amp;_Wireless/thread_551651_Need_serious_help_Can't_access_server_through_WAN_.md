---
title: "Need serious help: Can't access server through WAN ip"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by Linerah on 2007-09-15
Hello every, first I'd like to say thanks for taking a look here, I hope I put it in the right section. Anyways, I'll get straight to the point.

I have an old pc I installed ubuntu server edition on(newest version) then installed the gnome gui(im a linux newb). I have no problem accessing the server from within the lan.

The problem comes in when I (or others) try accessing it through the wan ip.

 I have Webmin configured to work with apache2. I have a linksys WRT54G router and my isp is comcast. Unfortunately, comcast blocks port 80. To get around this I have configured apache to listen to port 49300 (i know, odd number, but i wanted to make sure comcast didnt block it.) In my router, I have port 49300 forwarded to my server's static lan ip 192.168.1.109. 

So i tryed accessing my server through my wan ip (69.245.xx.xx:49300) and it failed to load. No biggie right, my router must not accept loopback. So i got ahold of some of my friends and had them try to access it through the wan ip (they were not on my lan, obviously) and it failed for them to. Now I am seriously confused.

So I use grc.com to see if my ports are open. Well, turns out that the port i was using (49300) was in stealth. I have know idea why, everything is forwarded and what not. So I think, maybe comcast randomly blocked that port, so i try to reset everything, except with port 49400. Same stuff, unable to access the server by the wan ip, inside and outside the lan. Stupid right? Get's worse.

On my other computer I have bit torrent running with port 49000 forwarded to it through my router, and it works fine. I test the port on grc.com, and it is open. So, trying to be smart, I change my bit torrent port to 30000 and then put my server on the open 49000 (forward to the correct ip's in my router and everything) then test the new bittorent port and it is open, then test my server's http port 49000 and it is set to stealth. W T F

So basically, my router does not/will not/isn't forwarding the ports i demand to my server. They are in there, but it's like the router ignores it, and doesn't forward them. I have tried everything I can think of to make it possible to access my sever by my wan ip, but nothing. 

I know this is really long, but i have spent the last 12 hours searching goggle, testing, trrying to get it to work, but to no avail. If someone could pleaseeeeee help, I would love you for ever. The way i look at it, everything should work, but doesn't. Simple as that. Unless I missed somethng, which i dont think i did. ANY insight at all would be very appreciated. Thanks.

---

### Post by whistl on 2007-09-15
A couple of simple things to double check.

Double check your router port forwarding rule to see what the destination port is set to.  If it's also 49300, then make sure your webserver is configured to listen on port 49300.  Run "netstat -ltn | grep 49300".  If you get no output at all, nobody is listening on that port.

The following example shows a service listening on tcp port 57609:

> 
$ netstat -ltn | grep 57609
tcp        0      0 0.0.0.0:57609           0.0.0.0:*               LISTEN     


It's possible your router's forwarding rule is sending wan connections to a different destination port, such as tcp port 80 (this would make sense, as 80 is the default port for web services).  If so, check that someone is listening on that port number instead.

Next, check that you have the correct default route on your server.  Without it, you'd only be able to access it from the local LAN.  Run "netstat -rn".  You should see something similar to:

> 
$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0 U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0            192.168.1.1  0.0.0.0             UG      0 0          0 eth0


The above example shows the default route pointing at gateway 192.168.1.1.  Yours may differ, depending on your LAN config.

---

### Post by Linerah on 2007-09-15
well i tested port 49300 to see if it was being listened to and i got this

tcp    0      0 0.0.0.0:49300      0.0.0.0:*    LISTEN

so I'm assuming it is being listened to. Also, when i navigate to 192.168.1.109:49300 it takes me to the server directory and at the bottom it says    

Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at 192.168.1.109 Port 49300


When i tested port 80, i got this

tcp    0      0 0.0.0.0:8080      0.0.0.0:*    LISTEN

it printed out 8080 and said it was listening to it, but nnot 80. Was that supposed to happen?

when i did netstat -rn i got this
  
Destination.....Gateway.....Genmask......................Flags........MSS window......irrt...Iface
192.168.1.0......0.0.0.0.......255.255.255.0.................U.................0 0..................0  eth0
0.0.0.0.............192.168.1.1.....0.0.0.0...........................UG.............0 0..................0  eth0

my gateway say 192.168.1.1, which is my router's lan ip. is that good? Thanks for the help a million, but im not sure how to interpret the results. The only thing that looks weird to me is that when i tested port 80, i got a response but it said port 8080 instead =\. Any more help would be very appreciated. Thanks for the help so far whistl :)

---

### Post by Linerah on 2007-09-15
I fixed it. I had everything right like I said. I just did a restored factory setting and did a hard reset of my router abd re input all the info and it worked. Thanks for the help though.

---

