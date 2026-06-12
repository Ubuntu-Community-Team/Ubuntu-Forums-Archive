---
title: "How do I set up Dynamic DNS?"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by FireFreek on 2009-10-03
Well I was messing around with my old computer and decided to install Ubuntu Server 8.10, and install torrentflux-b4rt on it. So far so good, i have SSH, Samba, and torrentflux working on it locally. But I was wondering how I could access from outside my home network, so I looked around and heard about dynamic DNS, but i'm still a little foggy as to how to get it to work.

---

### Post by nhasian on 2009-10-03
does your router support dynamic DNS?  if so you can just plug in your username/password/domain in there and it will auto-update for you.

---

### Post by carnagex420x on 2009-10-03
I've been using DynDNS for a while now and have never had a problem. My router also supports it so that makes life swell too.

---

### Post by stmiller on 2009-10-03
Yeah my router does it for me as well. DD-WRT ftw. :)

---

### Post by carnagex420x on 2009-10-03
> **stmiller said:**
> Yeah my router does it for me as well. DD-WRT ftw. :)

:lolflag: YUP!

---

### Post by FireFreek on 2009-10-03
OK I've got a dynamic DNS set up on my router, but now how do I get it to go to the torrentflux page when typing in the domain? Right now i access it by going to "http://192.168.2.15/torrentflux/html", but I want it to go there if i went to "XXXXX.dyndns.org".

EDIT: NVM, I got it to work using ddclient.

---

### Post by nhasian on 2009-10-03
I was just going to suggest forwarding the port in the router to your computer's IP address.

---

### Post by carnagex420x on 2009-10-04
DNS only resolves yor IP to a name. the subdirectories would have to navigated to directly, unless setup up differently.

---

### Post by FireFreek on 2009-10-04
OK well it seems I was half right. Ddclient updates the ip of the server with it's local IP(192.168.1.XXX), so it only works while i'm in my own network. Nhasian could you explain what you mean by forwarding the port(port 80?).

All my router takes is the host name, username and password, but even so it also only gives its local IP, because it's behind a VOIP modem that does some VERY basic LAN networking, and doesn't have dynamic dns settings. 

So my guess as to what to do is have the server figure out and update the public IP of my network, and to forward ports so that they go to the server?

---

### Post by carnagex420x on 2009-10-04
When you go to you domain name, you are going to your outside IP that is assigned to your router. In order to get inside you have to forward a port to the machine on the inside. If you forward port 80 to 192.168.1.102 on the inside the domain name is actually using the IP from the router and the router is doing the rest. Port forwarding is pretty straight forward if you need more help try Google. But heres an example.

test.com > router_ip > single_port_to_box > inside_box

Bad, I kno but hope it helps a little.

---

### Post by t0p on 2009-10-04
[DynDNS]("http://www.dyndns.com") offer a free service whereby your changing IP address is mapped to a host name.  So folk out on the internet can type your URL into their web browsers and get taken to your server.

---

### Post by halitech on 2009-10-04
If you need help with setting up the forwarding, here is a great resource

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

Just select your router, find the app you want to set up and it will walk you through the rest.

---

### Post by carnagex420x on 2009-10-04
If all you want to do is a web server, log into your router and find a tab that says port forwarding (it might be sectioned into single port, port range, or port trigger forwarding) and point single port 80 to your internal IP of the box.
DONE

---

### Post by FireFreek on 2009-10-04
OK then, i forwarded port 80 from my voip modem to my router to my server, and it didn't work.

---

### Post by carnagex420x on 2009-10-04
You dont need to touch your modem. If test.com can resolve to the IP of the router thats part 1. Part 2 is getting inside and thats all in your router. heres a better example.

---

### Post by FireFreek on 2009-10-04
Yes but my phone modem is evil and gives a local address to the router(and yet it only has one ethernet port, what genius came up with that idea?). I would put the phone modem behind the router, but that causes packet loss in my calls whenever I use the internet semi-intensively(youtube, torrents, online gaming, etc). It also happens as the network is set up now, but doesn't have packet loss, just some interference. My router is a Netgear WGR614v5, which is somewhat old and doesn't have QoS so I can't allocate bandwidth to solve the problem.

Current set up:

[CENTER]internet
V
Cable Modem
V
Phone Modem
V
Netgear WGR614v5
V          V
server     desktop pc


and somewhere in the cloud are various other things like a desktop, laptop, and wii.[/CENTER]




And yes, i already have ddclient set up with a domain from DynDNS, it just only works locally.

---

### Post by carnagex420x on 2009-10-04
Ok, so you have an odd setup... Before trying to use the domain name and routing in, I would try starting from the inside out. Use just IPs and go from local 192. address from inside your NAT to the IP of your router, then finally the IP of your modem or the domain name (because they should be the same). If you can get everything to work with IPs then the problem is your ddclient isn't updating your IP to DynDNS. But work your way outward and eliminate whats causing the problem as you go. Routing can be tricky.

---

### Post by FireFreek on 2009-10-05
Well I know the router is not the problem, as there is no problem connecting to the server using IP within the network, port forwarded or not. I think it is the modem, since when I forward port 80 on the modem to the router, I can't connect to the server using the public IP, which is given to the modem.

I do have one idea, but i'm not sure if it will work. My cable modem has an ethernet port and a USB port, and I think I can use the usb port to connect my server, bypassing the phone modem altogether. Speed isn't an issue for me, since I rarely go past 300KB/s with my server. Problem is, I don't know how to configure a USB connection with my server..

---

### Post by carnagex420x on 2009-10-05
Sounds like a solid idea, i nvr had to connect with a USB before but give it a try and see wats good.

---

