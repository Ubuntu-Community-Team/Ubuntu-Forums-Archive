---
title: "HOW-TO ssh over the internet"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by lazertek on 2008-07-15
setting up ssh over a LAN is pretty straight forward but when it comes to setting it up to be accessible over the internet it has a little more steps to it...

I have a router through which all my computers connect wirelessly/wired.... Now lets say I want to setup a computer in this network to be accessible by over the internet using ssh...

How would I do this... Remember that the computer is connected through a router that gives it it's ip address through DHCP....  A complete guide on how-to this will help me out along with a whole bunch of folks who have a hard time with ssh-ing over the internet...

---

### Post by stilus on 2008-07-15
Its pretty hard to write a manual, because this is mainly a router config thing. In general, you need to:

a) configure your ssh "server" to have a fixed IP address. Although this can be easily done on the system itself, your router usually does DCHP and can also be configured to always give the same IP to the same MAC address (this is based on your network card).

b) ssh goes over TCP, port 22 (normally). Often this can be done through NAT / PNAT (Might be called a dozen things, like "forwarding", "remote services" etc. etc.) in the router. What you need is something that looks like this:

```
INTERNET -> external port (TCP) -> router -> yourcomputer:port22 (TCP)
```

Mind you, choosing an external port somewhere above 1024 (which is not in use) could be smart: scripts trying to brute-force ssh (etc), usually dont bother looking on anything but port 22.

In my router I can choose a port range, (set them both to the same portnumber), a protocol (set them to TCP) and a destination (set them to the fixed address, which in my case is represented by the computer name I set when I created a fixed IP address in the router.


Good luck, and dont forget to backup your router config before you go messing about with it! ;)

---

### Post by lazertek on 2008-07-15
so the router has to be configured to allow ssh ... i'll check that out and see how it goes...

when connecting can you give a better example when you said INTERNET --> etc....

and example would be helpful understanding...

---

### Post by stilus on 2008-07-15
> **lazertek said:**
> so the router has to be configured to allow ssh ... i'll check that out and see how it goes...

when connecting can you give a better example when you said INTERNET --> etc....

and example would be helpful understanding...

As I said before, every router (and interface) is different. I'll give my THOMSON ST716v5 router as an example here (See attachment). 

If I'd added this entry (Called "games and application sharing" here) my router would be listening on TCP protocol on port 33322 and forward that to port 22 internally. 



Now, all I'd have to do is "Assign this Game or application to a local network device" (see attachment, bottom) and link this rule to the internal IP address of my ssh server.

Just to state the obvious: I should have sshd running on my ssh server, of course (apt-get install ssh would help ;) )

this way, I could do:

[B]
ssh -p 33322 me@myexternalip[/B]

thus doing:
[B]
INTERNET -> MyRouter, port 33322 -> MySshRerver, port 22[/B]

This is why its smart to first fix your DHCP to "always assign the same address" (done under Home > Home Network > Devices > yourdevice > Configure if you have a SpeedTouch 716.)

Mind you, every router -every incarnation of every router, it sometimes seems- does this differently.

Hope this helps (someone)...

---

### Post by lazertek on 2008-07-23
i will be trying this out soon and post back... sorry for the delay

---

### Post by zfh on 2008-07-23
1. you need to install openssh-server.
2. edit /etc/ssh/sshd_config
   to allow Port 22 (this is the port for ssh)
3. if you are behind a router (say you are using sbcglobal.net), you need to allow incoming traffics for Port 22. This can be done usind "firestarter"
   to install, use sudo apt-get install firestarter

---

### Post by sp0nge on 2008-07-23
I'm a little new to ssh, so please bear with me. 

I have also been working to make a server accessible via ssh. I have recently been able to connect from behind my router, but after I forwarded the port (changed from the default 22) this morning, I was unsuccessful. I believe my problem is that I forwarded a high numbered port, but did not change/add the port number in /etc/ssh/sshd_config. I don't know if that is the problem, but I changed that file and will attempt to connect again tomorrow.

---

### Post by BlueBuddie on 2009-11-13
Hello All,

I am  new to Ubuntu and ssh .  I am trying to ssh over a system in different network. The only port that is open is 80(http) .I cannot use port forwarding. 

I googled for solution but all I found was port forwarding in router .

Help me with this problem.

Thanks,
Blue

---

### Post by dentex on 2011-04-25
hi,
same situation as BlueBuddie.
On the system I want to reach via SSH, transmission BT client works only if set on port 80.
My WISP provides me an antenna that works as NAT.
LAN IP is fixed. External IP is bond to a hostname via DynDNS.
Only port 80 seems to be open from the outside.

thanks.

---

