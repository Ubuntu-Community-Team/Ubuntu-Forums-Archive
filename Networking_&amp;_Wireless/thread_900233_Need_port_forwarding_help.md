---
title: "Need port forwarding help"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by dfro on 2008-08-25
I have set up a LAN with local ssh, sftp, and scp.  Now I want to get remote access from outside the LAN working.

What I would like to do is set up a way for different incoming port numbers to be translated in the router to port 22 on the different computers on the LAN.

I would like to use a different port number to forward to each LAN host. Like this:

Listen on    -> Forward to
1.2.3.4:2001 -> 192.168.0.1:22
1.2.3.4:2002 -> 192.168.0.2:22
1.2.3.4:2003 -> 192.168.0.3:22

Is there a way to do this?  I have a d-link - EBR-2310 router. If this router cannot do this, can anyone suggest a router that can?

Thanks,
dfro

---

### Post by amo-ej1 on 2008-08-25
I know my Linksys wrt54g can do this by default and I'd be surprised if yours couldn't do the same, isn't there a port forwarding or 'applications'  tab in the configuration of your router ?

---

### Post by amo-ej1 on 2008-08-25
Or you could try google's first hit ... 
[http://portforward.com/english/routers/port_forwarding/Dlink/EBR-2310/Echolink.htm](http://portforward.com/english/routers/port_forwarding/Dlink/EBR-2310/Echolink.htm)

---

### Post by dfro on 2008-08-25
Yes,

I stayed up all night studying portforward.com and other sites.
It is a very good site. Everyone should also check out probemyports.com.  I learned a great deal about firewall security there.

What I want is the incoming external port on the router to be mapped to a different internal port on one of my LAN computers.

For example, 1.2.3.4:5000 gets forwarded/remapped to 192.168.54.1:22 for example.

All the examples I have seen do not show the external port being different than the internal port.  The IP address is what is changing only.

With so many programs and protocols designed to work on only one port, it seem impractical to forward port 22, for example, to only one computer in a LAN. It seems to me that what people would want is IP/port remapping.

In some of the sites that I studied, I heard mention of being able to remap the IP and the port to a different internal IP and port.

On my D-Link router, in the Advanced > Port Forwarding window, the "Start" and "End" boxes allow you to open up a range of ports in the firewall.  But, for external 1.2.3.4:5000-5008 would get mapped to internal 192.168.54.1:5000-5008. There is no ability to remap the port as well as the IP address. At least this is what I seem to be observing.

I can see why they call it port forwarding. Port 22 on 1.2.3.4 gets forwarded to port 22 on 192.168.54.1.  

It seems that what I want is "IP & port remapping", but I am a bit fuzzy on the correct terminology.

I guess I could reconfigure shh and shhd to listen on more than one port, but it would be simpler to let the router do it.

Thanks.

---

### Post by mellowd on 2008-08-25
It depends on your hardware, most consumer grade routers won't do this for you.


A far easier solution, is to change the ssh ports internally. Use 2212, 2213 and 2214 for example.

---

### Post by eldragon on 2008-08-25
if you just need port 22 on your LAN on different machines. just edit /etc/ssh/sshd_config and use a different port. 

your router should be able to redirect the same port number from the outside world to the inside :D

---

### Post by jimv on 2008-08-25
Nm

---

### Post by dfro on 2008-08-25
Thanks for the comments.

As per all of your suggestions, I am now trying to get my desktop to listen on multiple ssh channels, but I am getting a "Connection refused" error.

I have added another port to /etc/ssh/sshd_config on my desktop computer and restarted the ssh server, and now it is listening to a second port.

$ sudo netstat -antp|grep ssh 
tcp6       0      0 :::2000                 :::*                    LISTEN      5998/sshd       
tcp6       0      0 :::22                   :::*                    LISTEN      5998/sshd       
                 LISTEN      17205/sshd      
...

When I try to ssh from within the LAN to the d-desk computer from another computer, though, I get:

$ ssh d-desk -p 2000
ssh: connect to host d-desk port 2000: Connection refused

When I run the standard command:

$ ssh d-desk

The connection is successful.

I have done no port forwarding in the router, since my understanding is that nothing is blocked on the internal side of the router.

Thanks

---

### Post by dfro on 2008-08-25
Okay folks,

I am making some progress.  When I type into d-desk:

$ssh -p 2000 localhost

I get into my d-desk computer.  So, the computer responds to its own connection request on port 2000.  But, I cannot figure out why it is refusing a connection from another computer on my LAN.

Any ideas?

Thanks.

---

### Post by dfro on 2008-08-25
I found the solution!

It was computer d-desk's firewall settings (of, course) that were blocking me from making an ssh connection on port 2000.

I used the program lokkit to modify the firewall settings, which I am sure reside in the iptables and ipchains files.

In the lokkit screen, while leaving the security level checked on "high", I selected "Customize". In the new window, there is a section - "Allow incoming:" and an input area - "Other ports". I navigated to that area and typed in "2000".
The following command now works from a different computer on my LAN:

$ssh -p 2000 d-desktop

Now, I want to figure out how to close port 2000 and open a different port to accept incoming ssh connections.

And I will now also try to ssh to my public IP and port forward 2000 through my router to d-desk.

I hope all goes well!

A commercial grade patching/port mapping router would be a lot simpler.


Thanks.

---

