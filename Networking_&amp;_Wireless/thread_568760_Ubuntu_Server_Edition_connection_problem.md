---
title: "Ubuntu Server Edition connection problem"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by poisonmushroom on 2007-10-06
Hello, i'm new to Ubuntu and would like to ask for some help.

A friend of mine helped me set-up Ubuntu Server Edition, everything went OK. I Installed SSH on it so i can use putty from my laptop too. (Kernel Version 2.6)

The problem is, my friend cannot access my server through his computer (i made him a user), and he cant even ping it. I asked other people to try connecting it worked for nobody.

I went into my ADSL2+ modem configuration page to forward ports 22 and 80 using the servers IP, i also disabled the firewall, allowed UPNP, i updated the modems firmware to latest version, but nothing is working. nobody can connect to the server.

the ip is 192.168.1.34 if anoyne here wants to try.

Thanks in advance! :)

EDIT: pinging works for me only, but nobody else can find it / ping it

---

### Post by PilotJLR on 2007-10-06
Your friend really needs to read this:
[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)
;-)

from external to your LAN, SSH to your WAN ip address, not the local private address. This is assuming the port forward is setup properly.

---

### Post by poisonmushroom on 2007-10-06
Sorry but i'm not much of a pro, could you explain what exactly is going wrong? Is it the server? is it the modem?

Would be nice if you can explain! Thanks in advance! :)

---

### Post by leg on 2007-10-06
The ip you gave is a local network address and is not propogated onto the Internet. Your friend outside of your home network needs to connect to your routers external ip address. The router is then responsible for passing the communication onto your server. I would suspect also that you do not have a static ip address externally so you have another problem there.

---

### Post by PilotJLR on 2007-10-06
To find your WAN ip, visit [www.whatismyip.com](www.whatismyip.com)

Then have your friend ssh to that.
Like leg said, your server needs a static address so that the port forward doesn't break.

---

### Post by poisonmushroom on 2007-10-06
Alrite thanks guys, i solved the problem and found out the IP of my server.

My friend succesfully connected and we set up a counter strike server, which failed for some reason because after doing "./hlds_run -game cstrike -autoupdate +maxplayers 20 +map de_aztec > /dev/null 2>&1 &"
the server just, simply did nothing... (but 2 processes appeared when i did ps -A)

And also a new problem appeared after i restarted the server, my laptop and server show the same ip address.

I'm getting annoying, but i guess its just that im new to linux! thanks for understanding :)

---

### Post by xurios on 2007-10-06
The
> 
> /dev/null 2>&1 &

part of your command sends all of hlds_run output to a black hole (/dev/null), thus it seemed that nothing was happening, but you still had processes running from your command. If you want to see the output, try the same command without the > /dev/null 2>&1 bit. Also, the final & runs the process in the background, so you get a responsive terminal even though you started some process.

---

### Post by poisonmushroom on 2007-10-07
I will try it without dev/null, but first i have to fix my IP conflict... I have the same IP on both my server and laptop and i dont know how to fix it.

Thank you.

---

### Post by PilotJLR on 2007-10-07
Do you mean you WAN IP address (the one you found from [www.whatismyip.com](www.whatismyip.com)) is the same? Cause that is supposed to happen.

It's called Network Address Translation... one public address (the one found from [www.whatismyip.com](www.whatismyip.com)) is shared by many machines, with your router/gateway doing the ip translation.

---

### Post by poisonmushroom on 2007-10-08
What do you mean? Before they both had different IP's and at that time my friend used the servers ip to connect through putty. (I could connect to the server using the LAN ip)

But now they both have the same and my friend cannot connect, i mean if you ping the IP how can you get replies from 2 pc's? it can't be right.

I tried turning off NAT in my modem configuration, but after doing so the internet completely disconnected so i guess i have to keep it on.

Any other suggestions? Thank you!

P.S: Is a really old 128ram PC enough to run a CS 1.6 server using Ubuntu Server Edition?

---

### Post by PilotJLR on 2007-10-08
You're still confusing public and private addresses... please read the wikipedia link above, or just google it.

You must use NAT (unless you buy more public addresses).

You can forward port(s) from your public (WAN) IP address to any private local address.

For example, I can forward port 22 (ssh) to 192.168.1.2 on my private network (I am making up these addresses for example's sake). I can also forward port 80 (web) to 192.168.1.3. These are 2 separate physical machines.
If my public IP was 1.2.3.4, then you could then read my ssh machine through 1.2.3.4:22, and you could also reach the webserver at 1.2.3.4:80.

Same public IP address... different PORTS, different machines BECAUSE of the port forwarding rules.

---

### Post by poisonmushroom on 2007-10-11
I'm sorry, it seemes like i pissed you off but my since i lack a lot of knowledge when it comes to networking i find it difficult to understand.

I understood from your post that im in some sort of Private Network so both machines use the same IP address, and that IP comes from NAT, correct?

If so, is there a way to give each machine its own IP address? (not manually)

I forwarded the ports 22, and 80 using the LAN ip, 192.168.1.1 since the IP changes all the time i dont have to keep forwarding them on different IP's.

In order for me or others to acces the other machine (Ubuntu Server Edition) they must enter the ip, but it wont connect since its used by 2 machines so all i want is to give them both different addresses.

I copied some information from the modem configuration page, it might help you:

> 	WAN Information	 
 	    - DSL Mode: 	ADSL2+ Mode
 	    - IP Address: 	88.112.26.133
 	    - IP Subnet Mask:	255.255.224.0
 	    - Default Gateway:	88.112.0.1
 	    - VPI/VCI:	0/100
 	LAN Information	 
 	    - IP Address:	192.168.1.1
 	    - IP Subnet Mask:	255.255.255.0
 	    - DHCP:	Server

88.112.26.133 is the ip that is used by both machines.

P.S: In the port forwarding page there is a "Default Server" text with a box beside it with [0.0.0.0], has this got anything to do with the problem?

I hope i haven't been a pain in the ***, but it would mean very much to me if this is solved. Thank you.

---

### Post by PilotJLR on 2007-10-11
No, I'm not irritated at all! Sorry if it came off sounding that way! Just typing fast...

What you basically need to do is determine which ports you want forwarded where. Never forward anything to 192.168.1.1, since that is just an interface on your router.

Each computer in your network will have a unique address like 192.168.1.XYZ. This unique identifies them. ALL OF THEM, though, share a single public IP address (88.112.etc.etc.) and the router "hides" that fact from them. This is what permits them all on the internet at the same time.

You can forward each port on once, and to once machine. So if you forward port 80 (for web) to 192.168.1.10, then your "public" port 80 is now occupied. If you want to open multiple ssh ports, for example, you need to change the listening port on every machine except for 1. So then, you could forward unique ports to unique private addresses. For example, port 22 could go to 192.168.1.20, port 23 could go to 192.168.1.21, etc. In this example, the 192.168.1.21 machine would need to be reconfigured to accept ssh trafic on the non-standard port 23.

Hope this makes more sense... if you want to elaborate on what ports you want forwarded and why, then I could provide more relevant examples.

---

### Post by poisonmushroom on 2007-10-14
Your saying i should forward ports to each machine even though the IP's are dynamic? sounds kind of impossible to me.

But check this out, i looked around a bit and found out that i need to change the NAT mode from "SUA" to "Full Feature" if i had more than one public WAN IP, i did that and then the "Port Forwarding" page disappeared and some "mapping" thing came instead.

Thinking this will fix the problem, instead the internet stopped working on both machines and i got an error message in Windows saying something about an IP Conflict.

Since this is a linux forum, i suppose you wouldn't know? I'm off to bed now, got work tomorrow so i'l surf google for some solution! but i would be glad to see if you guys have any solution too.

Thank you!

---

### Post by PilotJLR on 2007-10-14
Nah, you're getting off the path again... remember on page 1 of this thread a couple of us asked  if the local addresses are static.  :-)
The private addresses must be static so that the port forward doesn't get broken once a new address is leased out.

Unless you purchased multiple public IP addresses from your ISP, then you must remain in NAT mode.

---

### Post by az on 2007-10-14
Does this help?
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by poisonmushroom on 2007-10-17
Thank you guys, i have read your posts and with a bit of fooling around i fixed the problem! now il just find me a good LAMP tutorial and try something with my first server! :)

---

