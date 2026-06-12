---
title: "SSH to foreign router through Ubuntu server"
date: 2017-02-15
forum: Networking &amp; Wireless
---

### Post by lynnden on 2017-02-15
So, I have a remote SSH connection to an Ubuntu Server machine about... 100 miles away and I'm trying to configure an email server on said machine. Trouble is, I need to get into the router, that's 100 miles away, to do some port forwarding to allow those ports to go through. 
Now if I were a sane person I'd have installed a VPN, or remote control on a computer on that local network to talk to the router, but I'm not a sane person, so I didn't. 
I have a couple questions, starting with:

CAN THIS EVEN BE DONE?


[LIST]
[*]Keep in mind that the OS that I'm talking to from 100 miles away is the Server version of Ubuntu, and, therefore doesn't have a GUI, so, it can't render "graphics" past ascii, so I can't do the linux equivalent of going into windows and setting up a remote desktop connection.
[*]The router in question is a "cisco dpc3848vm" it was stock from the ISP in the area.
[/LIST]
What do I need to do to set this up in any semblance of a timely manner?


[LIST]
[*]If there's packages that need to be installed on the Ubuntu machine to talk to the router itself
[*]Will there be any funny business to get the Ubuntu machine to communicate to the router?
[*]What's the process to do this sort of thing (if at all possible)
[LIST]
[*]Meaning, the installation process (if necessary)
[*]Configuration of any packages that'll be required
[*]Getting the Ubuntu machine to communicate to the router
[*]Getting the port-forwarding to happen.
[/LIST]
[/LIST]

---

### Post by TheFu on 2017-02-16
Welcome to the forums.

Can it be done?  That depends. How can the two Linux systems communicate right now?  Sounds like you want some sort of magic. There isn't any.  

One of the systems has to be a client and the other has to be a server. The server must be reached by the client. If ssh is the method for those connections, then there are options.  Ideally, the client is the machine you sit behind. I suspect because nothing was setup, you need to drive 2 hrs and do that.  Lacking that, can someone on the far end create a reverse ssh tunnel for you, so you can remote in, setup an ssh-server there, secure it, then do whatever port forwarding on the router is needed.

Clear as mud?

---

