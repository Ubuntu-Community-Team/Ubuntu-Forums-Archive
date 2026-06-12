---
title: "Accessing a machine behind a non-configurable router"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by DrCoolSanta on 2008-04-23
The scenario is that I have a machine in a place, and it is behind a router. The problem is that I have no access to the router and can't have this machine act as a server. This machine has servers like RSH, SSH, and VNC. When you first look at the list of servers, it would seem that it will be very insecure to allow this machine to have public access, but with help of a user here, named SpaceTeddy, I have been able to limit the number of people who can access this machine using the firewall (iptables) provided with Ubuntu.

Our goal is to be able to connect clients from outside the place with this machine. Now, it is not possible to do it the normal way, so I thought I would  set up a VPN. Since we have limitations, the only software that comes for linux, that I could use was Hamachi. When I tried using Hamachi, it seemed it could not connect with its servers, when I tried going to logmein.com, it didn't work as well. One could say that either the router blocks it or logmein does.

I finally concluded that people here could help me with this. If you can please do. More than being able to SSH to the machine, I want VNC or anything that provides us with a graphical display of the machine.

One approach i thought was that I could have the machine behind router keep trying to connect to one of my machines (acting as a VPN server) after every given interval, and whenever I need to connect to the machines, I could bring up the server. This approach however needs a lot of stuff, like setting up a Dynamic DNS account for my Internet connection has Dynamic IPs, configuring the server, etc. If this is a reasonable option, please help me accomplish this.

To be more precise, the server is running Feisty, why Feisty and nothing new? For some reason I can't update the server, and installing the new version of an OS is not the option here.

Even if you have very little help do give to me, I will be greatful.

---

### Post by SpaceTeddy on 2008-04-23
right-o, found your post :)

anyways... if you have no chance of connecting into the network, you need something that connects out. Do you have any way of getting a server/reliable host "outside" of your network that could be used a relay ? 
Also, are really ALL ports closed - is there not ONE port that can be connected to comming in. 

All you need is
a) an external computer which you can access from your internal network (port, protocoll, etc does not matter). The important bit is that your internal server can connect to it, and that the host if accessable on at least ONE port from anywhere on the net.

or 

b) one single incomming port - just one, tcp or udp... doesn't matter. You can pretty much tunnel anything over anything as long as you have one port and don't care about conventions :) 

If you have that, i have the solution [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127") - otherwise, i have no idea (but you know that already, since we already talked about it :)
Just thought i ought to add this information to the outside world so they can get some input aswell :)

---

### Post by DrCoolSanta on 2008-04-24
I'll have to contact the Univ if they have even 1 port open, if I would do that, I'd rather ask them why I can't use hamachi. And I can't have any other machine act as a server, but I can have it on temporarily, like in my first post in the thread, I just need some help to impliment it.

---

### Post by SpaceTeddy on 2008-04-24
helping you with implementing is no problem... but which way do you want to go ? external host or getting the uni to open a port ?

---

### Post by DrCoolSanta on 2008-04-24
[quote=DrCoolSanta]One approach i thought was that I could have the machine behind router keep trying to connect to one of my machines (acting as a VPN server) after every given interval, and whenever I need to connect to the machines, I could bring up the server. This approach however needs a lot of stuff, like setting up a Dynamic DNS account for my Internet connection has Dynamic IPs, configuring the server, etc. If this is a reasonable option, please help me accomplish this.[/quote]

How about this?

---

### Post by SpaceTeddy on 2008-04-24
mhm... ok.

that would mean you have internal host (call it A) and an external host (call it B). follow the steps of setting up the two hosts as described in the openvpn tutorial [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127")
you only need part 1 - part 2 is not for your setup :)

One slight change is there to - in the configuration of B, instead of specifying the remote, specify a local IP where IP is the local IP address A will be connecting to.
the rest is pretty much the same. Tell me how it progresses :)

[EDIT]
also leave out step 8 (you already have a configured iptables ruleset).

---

### Post by DrCoolSanta on 2008-04-25
Dynamoc DNS, so I should probably set it up with hosts?

---

### Post by SpaceTeddy on 2008-04-25
mhm - you need a dns or hostname for the external (outside uni) machine. I personally use no-ip.org, but you are quite free to use any other hostname - as long as you have something that you can use to connecto the external machine with :)

---

### Post by DrCoolSanta on 2008-04-25
I am setting up my univ pc as A and home pc as B, your post here probably asked me to do it the other way round, but I was in the univ when i started doing this. You said in the same post earlier that on my home PC, I should set the PC to connect to as the internal univ IP for the univ PC?

EDIT: Reading it again, it seems that I have to set the configure the home PC with my home pc's internal IP. That's what i have set it too. I am probably going to call up someone in the univ and stay at home, with her doing the work needed to be done there, and I'll do the work at home and any debugging. I'll update you on the progress then only. By the way, Home PC refers to the external server, just in case you got confused.

EDIT2: Please also tell me what should be the config of the port forwarding rules on the home server. I am currently doing 1194.

EDIT3: -_- Now I feel like I am stupid. The 7th step, please explain. I think the 7th step is probably unimportant here, because I only need connection from one machine to another, where one is a router and another is just a machine, I won't need any direct access to any machines in the network, and if by chance I will ever in a blue moon need to do so, i will just connect to the router by SSH and SSH to the nodes. Probably it is unimportant here. I would guess you thought that was very important here because you knew that my univ machine was a router but my only concern is the master node, so its pretty much not needed (and you actually didn't write it for me, its just a general thing so . . .)
Also my univ pc uses 192.168.0.x IP addresses, at home I use 192.168.1.x and 10.0.0.x both (ADSL router connected to wifi) and so the tun0 config has become 192.168.5.1 and 192.168.5.2, I hope that's not going to cause problems.
PS. This was an edit, due to a feature that I needed, I got rid of the 192.168.1.x, somebody said that netgear's auto update DDNS feature requires bridge mode to get the actual external IPs.

---

### Post by SpaceTeddy on 2008-04-26
> **DrCoolSanta said:**
> I am setting up my univ pc as A and home pc as B, your post here probably asked me to do it the other way round, but I was in the univ when i started doing this. You said in the same post earlier that on my home PC, I should set the PC to connect to as the internal univ IP for the univ PC?

which was around does not realy matter. The Important but is that the one at home is NOT trying to connect anywhere, but only wainting for connection (having the remote changed to local), since it cannot contact your uni PC anyway.
Which way around does really not matter - at all. This is a symmetrical connection :)
> **DrCoolSanta said:**
> 
EDIT: Reading it again, it seems that I have to set the configure the home PC with my home pc's internal IP. That's what i have set it too. I am probably going to call up someone in the univ and stay at home, with her doing the work needed to be done there, and I'll do the work at home and any debugging. I'll update you on the progress then only. By the way, Home PC refers to the external server, just in case you got confused.

i'd install ssh on the home PC, then go to uni and ssh back home. This way you have both computers under controll at the same time and can work on both simluatinously. It's way faster than calling someone up :) 

> **DrCoolSanta said:**
> 
EDIT2: Please also tell me what should be the config of the port forwarding rules on the home server. I am currently doing 1194.

port forwarding ? i guess your home network as a router that has to forward packets... well, the ports used are the one specified by rport and lport. You can just take these out (which will cause openvpn to default to port 1194). It does not use anything else... 
How you put the rules into your home-router i don't know... there are one million different boxes out there, and i can't possibly know them all. 
So, in general, take out the rport and lport specification on both hosts, and then forward port 1194 from your home router to your external server. Also, i'd forward ssh to connect to it indipendantly in case the VPN does not work. SSH always works... almost always anyways :)
> **DrCoolSanta said:**
> 
EDIT3: -_- Now I feel like I am stupid. The 7th step, please explain. I think the 7th step is probably unimportant here, because I only need connection from one machine to another, where one is a router and another is just a machine, I won't need any direct access to any machines in the network, and if by chance I will ever in a blue moon need to do so, i will just connect to the router by SSH and SSH to the nodes. Probably it is unimportant here. 

if that is your scenario - yes it is unimportant ! Step 7 is to make the two router act as gateways for the remote network, enableing all clients to know where the other network is without changing their configuration. I should really edit that part and explain more, but it would result in A LOT of explaining, as it requires to understand how routing in general works. 
> **DrCoolSanta said:**
> 
I would guess you thought that was very important here because you knew that my univ machine was a router but my only concern is the master node, so its pretty much not needed (and you actually didn't write it for me, its just a general thing so . . .)
Also my univ pc uses 192.168.0.x IP addresses, at home I use 192.168.1.x and 10.0.0.x both (ADSL router connected to wifi) and so the tun0 config has become 192.168.5.1 and 192.168.5.2, I hope that's not going to cause problems.

not at all. The IP's they use between the two must not match any other network directly accessable over the net (in your case that means it cannot be the 192.168.0.x network and not the 192.168.1.x network. The 10.0.0.x is a precaution taken, but it will (normally) not get in the way (unless you use wifi :) )

> **DrCoolSanta said:**
> 
PS. This was an edit, due to a feature that I needed, I got rid of the 192.168.1.x, somebody said that netgear's auto update DDNS feature requires bridge mode to get the actual external IPs.
there i do not know what you are talking about... really, no idea :(

AS a sidenode - send me a picture with the layout of your networks (only the imporant bits) as well as your two openvpn configurations. I'll look over them and see if they should work (in general) or not.

hope we get this to work :)

PS: I hope you're subscribed to this thread :)
PPS: i answer here and not on priv because this post might help someone else besides you when reading it...

---

### Post by DrCoolSanta on 2008-04-26
Well I had the idea about using ssh as well, seems like I am going to keep ssh with vnc on my computer, so that I can show off in school ;).

And I didn't expect you to reply to the PM, I was expecting it here, because the purpose of a forum is to actually help people out and it is actually more of an archive of problems, so people can check if the solution is there . . .

---

### Post by DrCoolSanta on 2008-04-26
Well I had the idea about using ssh as well, seems like I am going to keep ssh with vnc on my computer, so that I can show off in school ;).

And I didn't expect you to reply to the PM, I was expecting it here, because the purpose of a forum is to actually help people out and it is actually more of an archive of problems, so people can check if the solution is there . . .

EDIT: Oops, for some reason it said that it couldn't be posted, so I reposted . . .

---

