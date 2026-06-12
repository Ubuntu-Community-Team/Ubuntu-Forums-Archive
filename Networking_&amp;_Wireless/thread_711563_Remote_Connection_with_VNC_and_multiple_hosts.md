---
title: "Remote Connection with VNC and multiple hosts"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by TorchlightJay on 2008-02-29
Hello,
  I am wanting to do something interesting with remote connection. In the past I have used putty for SSH tunneling and VNC. It has worked pretty well in the past.  The problem is now I have a lot of clients to connect to. In one network I have like 30 people and really one gateway. Now it can become troublesome to try and log into the gateway everytime and change the port forwarding to that IP so I can use VNC. 

What I want is to find a more efficient way to connect to people using VNC and SSH. That way even if they have 500 people (figuratively speaking of course), I can connect almost seemlessly rather than having to connect to the gateway and have to move the port to different IPs. 

Can you think of any way to do this more efficiently? I was wanting to see if I can do it via PPTP or something. Any ideas are appreciated.

---

### Post by Mr. C. on 2008-02-29
Configure your ssh server to allow gateway ports.  See GatewayPorts in man sshd_config.

With GatewayPorts enabled, you can tunnel to any IP on the LAN by simply creating the tunnel to the gateway.

Alternatively, you can create a VPN, which makes the remote IP space available to your apps.

---

### Post by TorchlightJay on 2008-02-29
Okay so let me see if I get you straight. 

By ssh server, do you mean the machine I want to connect to, you know the host. Do you mean that i need to setup a completely separate server for SSH usage? So i need to make my changes to sshd on the host or this completely separate server? I read through it and I am still not 100% sure on how it works? I need to bypass the gateway since i can't forward a billion ports. I don't fully understand it all though. 

Also, i wnat to set it up to where someone could send me a message saying yo know "my computer is busted, can you fix it?" and then i can respond very quickly and connect to the person's host machine. of course, it'd be easier if i could bypass using the gateway and forwarding ports.

---

### Post by Mr. C. on 2008-02-29
I don't know what hardware your client's have, nor how many clients you have.  So you'll have to describe that better to give you a clear set of choices. 

So let's assume you have 1 client, with lots of people inside.  We'll call this the client network. Here are the basic options:

1) SSH server runs on machine on client's network.  You cannot to that SSH server through their router, which you have pre-configured to allow SSH traffic to pass to the SSH server you setup and manage on their network.  What GatewayPorts set, you will be able to VNC connect to any of those systems.  (there are other virtual desktop solutions that work here too).

2) VPN connection.  You setup client's router to provide you a VNP connection.  This puts you on your client'sLAN, where you can access any IP on the clients LAN.

3) Create an UltraVNC SingleClick app that client launches when they need help.  You run Listening mode VNC viewer on your workstation, and setup your firewall to allow their incoming request.  A dialog appears on your desktop asking your permission to see their screen.  You allow incoming connection, and the two of you are sharing the screen.  This option is easy for many, and allows customer's to be in control.  It is also cheap, in that you don't have to buy VPN hardware or setup a client SSH server.  See here for more info if this option interests you: [http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)

---

### Post by TorchlightJay on 2008-03-01
Sounds like a plan. Now let's take situation number 1. I put on an ssh server, do I need to put an SSH client like putty on all the clients and have them connect to server. Then when I need to do a VNC, I simply connect to the one server and then from there go to the specific client? How do you differentiate from clients on the SSH server? Does the server need to be in their office or can it be offsite but they still connect to it via a client like putty?

On number 3, am I still able to use SSH to create a tunnel for security sake. Do you know of a way I can integrate it onto a webpage for trouble ticketing? 

Some clients have VPN, some have nothing but your simple run of the mill routers, I want to keep options open for all scenarios and remain secure. My main thing is making it convenient for them to tell me that there's a problem and make it simple for me to identify their system and connect to them conveniently. All three seem like they can work. 

Thanks

---

### Post by Mr. C. on 2008-03-01
Here's the answers:

1) the SSH server needs to be on their LAN.  So if you have 10 clients, you need 10 SSH servers, one on each client's LAN.  This is a lot of work and trouble.  I wouldn't go that route unless they already had a support infrastructure that could ensure the SSH server was up and running!  Each desktop in each client will need some virtual terminal app running, be it VNC server, Remote Desktop, or Windows NetMeeting.  SSH gets you in securely, then you connect to the desktop client.  Let's leave the rest of the SSH-based questions until you've decided which route to go.

2) There is no SSH tunnel here.  Instead, can build in encryption into the client app you create and distribute to your client's desktops.  You could integrate this into a web page, where they just click on a link and it launches the app!

3) For those clients that have a VPN - configure it to allow what access you need and use the VPN to securely connect.  Then, use the remote desktop app of your choice, like those listed in (1) above.  Frankly, I have insisted on remote access via VPN if client's have wanted faster assistance.  If your client can't afford a VPN capable router, maybe you should consider how much they are worth to you! :-)

Hope this helps.

---

### Post by TorchlightJay on 2008-03-02
Hey, A VPN capable router is a good idea, I will agree. I do like the Ultra-VNC Single Click to (haven't tested it yet). Any particular vpn router to get? What kind of client would i need and is there like extra components (software and/or hardware) that i need?

Once that's setup, i just connect via a VNC or Remote Desktop Protocol client? Movin' along, is there a way to figure out which customer is requesting and to automatically collect (besides Ultra-VNC)

---

### Post by Mr. C. on 2008-03-08
Sorry for the delay - do you still need help with this ? 

I can't give advice on hardware, as you've not specified a budget nor requirements.

---

### Post by itsu207 on 2008-03-08
I do not how impatient your clients are, but I think you can use vncjava for a browser based connection. It will not be as fast as plain vnc, but fairly workable for me, from office.

---

### Post by TorchlightJay on 2008-03-09
Sorry for a slow response on my end. 

Hardware wise, let's say for the sake of argument, they only want to spend $100-$200. Is that doable or do they need more. The requirements I guess would be just VPN. Let's say that they want VPN I tell them we need to put in a device on the network to allow it (assume they have a router already, just not one VPN capable). This would be the scenario I guess.

---

### Post by Malikius on 2008-03-09
I am trying to learn how to install programs and am lost. I am trying to install and use TightVNC. And asked on Mepis and they weren't any help. Can somebody, PLEASE. Give me a step by step method on how to download which programs and what exactly do I do to get these program(s) up and running. 

I tried to look up VNC in the file/folder area to see if it would find these files that I heard comes with Mepis 7.0 . Somebody please tell me how to install programs.HELP!

---

### Post by Mr. C. on 2008-03-10
> **TorchlightJay said:**
> Sorry for a slow response on my end. 

Hardware wise, let's say for the sake of argument, they only want to spend $100-$200. Is that doable or do they need more. The requirements I guess would be just VPN. Let's say that they want VPN I tell them we need to put in a device on the network to allow it (assume they have a router already, just not one VPN capable). This would be the scenario I guess.

Sure, there are plenty these days.  Have a look at :

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130276636538&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3653843097B02](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130276636538&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3653843097B02)

Take a look at the User Guide PDF on that page, esp. Chapter 2.  It will  help you a great deal.

If they already have a router that does not support the VPN, you'll have to configure it to allow certain ports to pass through (IPSEC), or just replace the router with something like the one in the link.

It's hard to advise without knowing detailed requirements; without these, its just a guessing game.  I hope the info here helps you refine your requirements and moves you closer to your end goal.

---

### Post by Mr. C. on 2008-03-10
> **Malikius said:**
> I am trying to learn how to install programs and am lost. I am trying to install and use TightVNC. And asked on Mepis and they weren't any help. Can somebody, PLEASE. Give me a step by step method on how to download which programs and what exactly do I do to get these program(s) up and running. 

I tried to look up VNC in the file/folder area to see if it would find these files that I heard comes with Mepis 7.0 . Somebody please tell me how to install programs.HELP!

Perhaps you should start your own thread, so that the original poster and those responding don't get distracted .  Be as specific and clear about your goals; the details in this post here are not clear enough to assist.

---

### Post by TorchlightJay on 2008-03-12
Cool. 

So you mentioned requirements. I am not sure what you want to know so I will do my best to get this going.

Say that I have a customer with a network dealing with 15 computers. They are all behind one gateway. They have no VPN setup but want me to be able to remote connect to their system in order to fix it. On my end, I want to know whom to connect into and their network information (ip address, port, etc). On the same token, I want to know what their problem is so that I can just get working rather than calling people or emailing them to figure out what's going on. 

I am familiar with VNC and it has worked in the past. I have used SSH to secure the connection into people's computers. That works fine when it's one or two computers but when it's 15, I can't have 15 ports open for both ssh and vnc. I just needed something convenient.

---

### Post by Mr. C. on 2008-03-12
Create the desktop applet I mentioned, which allows them to initiate a help session: you simply open a port on your firewall and listen.  You will see the machine connecting via announcement dialog.

If you need to proactively work on their systems without their intervention, then best thing would be to purchase a VPN device like I indicated in the link, configure it and gain some experience using VPNs.  Once connected, you'll be on their LAN, so you connect to whatever machine on the LAN you want via IP or hostname (depending upon how you do name services).

On EACH of their machines, you need some remote desktop service enabled, be it VNC, Windows Remote Desktop, or the old but usable NetMeeting.  Each has strengths and weaknesses.  Windows Remote Desktop effectively logs them out of their session on their screen, and gives you control at that point.  VNC is a shared desktop, as is NetMeeting (no logout, so you don't disturb them).

Again, you need to gain experience *doing* before you'll understand strengths and weaknesses of any solution; this will allow you to better refine your expectations and requirements.

SSH doesn't sound like the right way for you to go - why have another machine running that you have to maintain, just to provide essentially what a hardware-based VPN appliance does for you?

---

### Post by TorchlightJay on 2008-03-12
Thanks. I will have to try these options out.

Now the application you are talking about, you mean that single click ultravnc thing? How would I setup the network? I really don't want to have to forward all these ports and what not. Is there a way for it to automatically open the port or connection without me having to mess with the gateway/firewall?

---

### Post by Mr. C. on 2008-03-13
Yes, it was the single click ultravnc program.  You open 1 port (5500) on your firewall.  Multiple connections will connect over that port.

> How would I setup the network? 
I don't know what you are asking.

---

### Post by TorchlightJay on 2008-03-13
By "how do I setup the network" I mean, how do I set it up to where all users/client connect to port 5500? Which IP do I forward port 5500 to? You mentioned setting it to listen, how do I do that? I am sure it's different with each router but I am sure there is some similar underlying concept. Any help you can provide will help. Thanks.

---

### Post by Mr. C. on 2008-03-13
Its a simple port forward on your router.

It is worthwhile reviewing the documentation on the UltraVNC site as to how to run in listening mode and how to create a single click app.  Its all documented for you there, and seems not necessary to retype here.

---

### Post by TorchlightJay on 2008-03-22
Hey things seem to be working pretty fine right now. I have a question. What if I had a client whom had a notebook. They are not always on the same network. How can I get that setup to where I can connect regardless of what network they are on? Thanks.

---

