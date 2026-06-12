---
title: "broadcasting my apache2 server on the web"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by manuleka on 2009-12-10
ok installed apache2/mysql/php for testing purposes on my machine... 

everything seems to be functioning as expected... now i'm going to test wordpressmu/buddypress... i would like a client to get access to my server (from his pc through the internet)

so i figured i need to setup my router for port-forwarding... i'm using a DSL-604T Gen II router... i have played with port-forwarding once before in setting up on another router for VNC Remote Desktop

so using that experience i set up a port-forwarding rule (using virtual server option on my router settings) to 
```

port-start:80 port-end:80
port-map:80 port-map-end:80

```

can someone correct me on the above numbers please... 

and also do i need to disable/enable something else so my server can be viewable through the web??

---

### Post by HighCommander540 on 2009-12-10
> **manuleka said:**
> ok installed apache2/mysql/php for testing purposes on my machine... 

everything seems to be functioning as expected... now i'm going to test wordpressmu/buddypress... i would like a client to get access to my server (from his pc through the internet)

so i figured i need to setup my router for port-forwarding... i'm using a DSL-604T Gen II router... i have played with port-forwarding once before in setting up on another router for VNC Remote Desktop

so using that experience i set up a port-forwarding rule (using virtual server option on my router settings) to 
```

port-start:80 port-end:80
port-map:80 port-map-end:80

```

can someone correct me on the above numbers please... 

and also do i need to disable/enable something else so my server can be viewable through the web??

That is all you need to do, just make sure that the rule says to send the requests to the IP address of your server on your local network.

---

### Post by manuleka on 2009-12-10
> **HighCommander540 said:**
> That is all you need to do, just make sure that the rule says to send the requests to the IP address of your server on your local network.

ok... i think there's still some setting on the router that needs altering because when i type my router ip (isp provided ip) i get the my router login/password prompt which gets me to the router page...

although all those testing was from machines on my local network... haven't got a chance to test it from an outside machine... 

anyone here with a DSL-G604T router that can help? i've been going through it's manual and stuff with no luck :(

---

### Post by OffAxis on 2009-12-10
sounds like you're port forwarding the WAN IP (isp provided one) to the ROUTER's internal IP and not your server's.
Routers typically use something like 192.168.1.1, whereas your server should be something like 192.168.1.2.

---

### Post by manuleka on 2009-12-10
> **OffAxis said:**
> sounds like you're port forwarding the WAN IP (isp provided one) to the ROUTER's internal IP and not your server's.
Routers typically use something like 192.168.1.1, whereas your server should be something like 192.168.1.2.

my pc's ip in my local network is 10.1.1.10

my router's isp provided ip is xyz.xyz.xyz.xyz

i thought i'm just forwarding port 80 to 10.1.1.10?

there is a webserver (tcp-port 80, 443) option on port-forwarding (virtual server) on my router which i have enabled for ip 10.1.1.10

---

### Post by HighCommander540 on 2009-12-10
> **manuleka said:**
> my pc's ip in my local network is 10.1.1.10

my router's isp provided ip is xyz.xyz.xyz.xyz

i thought i'm just forwarding port 80 to 10.1.1.10?

there is a webserver (tcp-port 80, 443) option on port-forwarding (virtual server) on my router which i have enabled for ip 10.1.1.10

Well I am sorry that is not working, but it must be something with your router. I do have an idea on what might be causing it.

I don't know about your router, but mine use to be really dumb before I got a new one. Especially when I was just using it with an IP address and not a domain name. Try accessing it from outside your network. It wouldn't let me do it with my IP address from inside the network. From outside though I could access it.

---

