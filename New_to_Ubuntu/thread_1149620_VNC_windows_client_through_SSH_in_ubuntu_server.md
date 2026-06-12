---
title: "VNC windows client through SSH in ubuntu server"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by televisi on 2009-05-05
Hi Guys,
Can I connect to my Ubuntu server using SSH and run VNC / Tight VNC to control client that is located inside Ubuntu Server's LAN?

ie:
1. computer A => master / VNC client
2. computer B => Ubuntu server (giving SSH capabilities)
3. computer C => XP under same netmask and IP range with Ubuntu server / VNC Server

Thanks

---

### Post by freak42 on 2009-05-05
I am not sure I understand your setup correctly.

As a more general answer: You can create 'ssh tunnels' which for instance allow to forward traffic into secured networks, which you can't access otherwise from outside.
There are many tutorials on the net about it.

hth

---

### Post by Hospadar on 2009-05-05
If I understand you right then yes you absolutely can.

The xp machine and ubuntu server are connected to the same router yes?

The client you want to connect with is outside that router yes?

if that's the case, then you'll need a couple things:

- openssh-server installed on the ubuntu server
- a vnc client installed on the ubuntu server
- some vnc server on the xp server
- port 22 needs to be forwarded on the router to the ubuntu server, you also need to know your server's external ip
- an ssh client on the client machine
- an X server on the client (if it's not a linux machine)

if you're in ubuntu, and I'm just going to assume you know how to ssh, if not, look it up in the docs link in my sig, it's easy.  ssh into your server and start up the vnc client pointed at the xp machine.  Make sure you are using X11 forwarding.  in ubuntu or osx, this means adding a "-X" or "-Y" argument to the ssh command, in windows it depends on your ssh client.

With X11 forwarding, the vnc will open up on your windows client.  This will be really slow.  VNC is slow to start with without all the extra redirection.  That said it will probably be usable.  If you are doing this to get some windows programs in linux, I would STRONGLY suggest you use a virtual machine like virtualbox instead, it will be much faster (unless your client is really slow) and more responsive.  If the programs you need will work under wine, even better

---

### Post by televisi on 2009-05-05
Yes, this is basically I want:
Master PC remote from outer world (ie: 209.134.777.888 ) connect to cable/adsl modem (ie: 192.168.0.0) through Ubuntu server (ie: 192.168.0.1) using SSH to remote any XP clients (ie: 192.168.0.10,  192.168.0.5, 192.168.0.9) that is located within the same network of Ubuntu server 

As you can see, XP clients are dynamic.
The question is how do I port forward VNC port from ubuntu server to at least 1 XP client? I know it'll be more difficult to automatically detect which XP IP I want to connect, but let say, can I manually configure (ie start/stop port forwarding service) so that I connect to the one I want.

I've setup SSh server as normal SSH CLI connection, now I need to do the rest.

You mentioned installing VNC client in ubuntu server, will this work as mine is full CLI server?

And what is wine?

Thanks heaps!!
> **Hospadar said:**
> If I understand you right then yes you absolutely can.

The xp machine and ubuntu server are connected to the same router yes?

The client you want to connect with is outside that router yes?

if that's the case, then you'll need a couple things:

- openssh-server installed on the ubuntu server
- a vnc client installed on the ubuntu server
- some vnc server on the xp server
- port 22 needs to be forwarded on the router to the ubuntu server, you also need to know your server's external ip
- an ssh client on the client machine
- an X server on the client (if it's not a linux machine)

if you're in ubuntu, and I'm just going to assume you know how to ssh, if not, look it up in the docs link in my sig, it's easy.  ssh into your server and start up the vnc client pointed at the xp machine.  Make sure you are using X11 forwarding.  in ubuntu or osx, this means adding a "-X" or "-Y" argument to the ssh command, in windows it depends on your ssh client.

With X11 forwarding, the vnc will open up on your windows client.  This will be really slow.  VNC is slow to start with without all the extra redirection.  That said it will probably be usable.  If you are doing this to get some windows programs in linux, I would STRONGLY suggest you use a virtual machine like virtualbox instead, it will be much faster (unless your client is really slow) and more responsive.  If the programs you need will work under wine, even better

---

