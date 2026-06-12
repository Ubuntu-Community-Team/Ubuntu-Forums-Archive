---
title: "Help setting up Remote desktop (VNC)"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by frekimedia on 2007-11-25
Hey, I'm running Ubuntu 7.10 desktop ed on both my laptop and my desktop. I'm trying to set it up so that eventually I can pull up my desktop while I'm on my laptop at school (remote desktop). I tried following the instructions found here [MaddHat]("http://maddhat.com/?p=15"), but whenever I try it out locally I get "Unable to resolve host by name: Connection timed out (110)".

the command I use is
```
vncviewer ****-desktop:0
```

What am I doing wrong? BTW, it works the same way vice-versa (when I try and access the laptop via VNC).

---

### Post by frekimedia on 2007-11-25
Does anyone have any ideas? I also forgot to mention that I went into **System > Administration > Login Window** and set the remote style to 'Same as local'

---

### Post by frekimedia on 2007-11-25
Seriously...no help?

---

### Post by frekimedia on 2007-12-04
Seriously, I need help setting this up. What I want to do is be able to access my network from outside the network (like while I'm in class trying to stay awake). If anyone can help me, I'd love it.

---

### Post by allnightarockin on 2007-12-05
First, it mat seem like a dumb question but its better to start off this way to get backround information
what vncserver application are u using on your home computer. (the one you connect to from school)
just the built in vncserver app??
And when your at school are you typing the local ip (like 192.168.1.xxx) cause that only applies to your local network..
I think the default vncserver doesnt have a password protection the session has to be allowed by the computer your connecting too. which wouldnt do u much good if your not in reach of it..
But vnc should be simple to work on.

Terminal: vncserver  < Computer your connectioning too
Terminal: vncviewer < Computer your connectioning from

Do you have port forwording on??

---

### Post by fishbolt on 2007-12-06
The message you are receiving is about host name resolution and thus you probably have DNS or general networking problems. Without knowing the layout of the network(s) involved in your situation it is difficult to provide any advice.

---

### Post by frekimedia on 2007-12-24
Thanks for finally providing a little insight! I just use the built-in vncviewer to connect remotely while abroad from my laptop, which has the same Gutsy Ubuntu install as my desktop. I use the external IP to connect (it's not a 192.168.xx.xx number).

As for the reference to the DNS problem: funny you should mention that because I'm always getting DNS errors popping up. Is there perhaps some underlying DNS issue I wonder? I'm not a network expert by a long shot so I have no clue. 

The network in my house is set up via a cable modem and two Netgear 802.11g wireless routers, one of which is being run just as a switch and the other one which handles all the actual routing duties. No modifications done on those btw.

Does any of that help?

---

### Post by AgentZ86 on 2007-12-24
My guess is that first you need to setup port forwarding within the router to allow outside access to get thru to the PC behind the router.

I'm not as familiar with the VNC but I would toy with the System/Preferences/Remote Desktop  Features of Ubuntu And try it out.

Then from there you may also need your router IP address, or perhaps the ISP's IP address given to you at your remote locations, And if it's a dynamic IP this could change regularly. I'm not 100% sure this part all applies to VNC connections but I would invite some more input on this also.

My request is:
Please advise on a general setup/ or typical setup topic of Remote Desktop access.

Remote Desktop is behind a router, and wanting to access the remote desktop via laptop from another location outside of the local network.Access via www.
Please advise

P.S I wish I could be of more help on this, I'm more knowledgeable about webhosting and email servers then VNC:popcorn:

---

