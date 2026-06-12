---
title: "Remote Access - almost there"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by schmidtbag on 2008-10-14
Just so you all know, I do have remote access working, through a wireless LAN.  I have Ubuntu configured so its not just local computers that can connect to me.  But I can't figure out for the life of me how to connect to my computer when I'm not in a LAN.  I have vncviewer, for Windows computers.

What is the code I'm supposed to use in vncviewer.exe to connect somewhere else?  Being in a wireless network, this makes things twice as tedious for me to solve for myself.

If its more than just a code I need a step by step tutorial on how I'm supposed to get this to work.

Thanks a lot in advance.

---

### Post by cariboo on 2008-10-14
You have  to have a remote desktop server of some sort running on your Ubuntu computer. X11vnc is available in the repositories, you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it. Once the sever is running, you can connect just like you would to your windows computer.

Jim

---

### Post by _sebastian_ on 2008-10-14
Hi schmidtbag,

when you are interested in connecting (?)ubuntu to (?)ubuntu you could have a look at this project [https://launchpad.net/remote-help-assistant]("https://launchpad.net/remote-help-assistant") where we try to make it simple for everyone. 

The project is still in an early phase but you might give it a whirl :)

---

### Post by schmidtbag on 2008-10-14
I don't get it, nothing worked.  I ran x11vnc in terminal and it outputed:

The VNC desktop is:      Tornado-II:0
PORT=5900

which I told someone else to input "Tornado-II:0" and got no connection.  Is that wrong?  Am I supposed to do more with x11vnc?



@sebastian
if this was ubuntu only I probably wouldn't have had a problem in the first place haha

---

### Post by krunge on 2008-10-14
> **schmidtbag said:**
> I don't get it, nothing worked.  I ran x11vnc in terminal and it outputed:

The VNC desktop is:      Tornado-II:0
PORT=5900

which I told someone else to input "Tornado-II:0" and got no connection.  Is that wrong?  Am I supposed to do more with x11vnc?


If the machine's hostname 'Tornado-II' does not resolve via name-lookup (DNS), tell them a hostname that does, or an IP address they can reach.

E.g. if the machines IP number is 24.56.78.90 and is reachable by them they should use "24.56.78.90:0".

---

### Post by schmidtbag on 2008-10-14
but, if i'm through a router how is that supposed to work?  because the address i currently use through the lan is only visible in that network, not the whole world.  i went to "whatismyip.com" and that doesn't work either, and i'm pretty sure i tried the :0 part.  is there something else?

---

### Post by _sebastian_ on 2008-10-15
well I am not 100% into the details but if done correct your router will 'route' the traffic trough to you computer.

For this you router either needs to support UPnP or you have to tell the router which ports to route (incoming and outgoing).

So when you request something from the net the router will translate your internal IP to his external and pass it on. Once you get a 'response' or incoming traffic the router will do the same thing the other direction.

Please correct me if I am totally wrong here but this is how I understand it :confused:

So you have to check your UPnP settings and make sure that the router is doing NAT (network address translation)

---

### Post by schmidtbag on 2008-10-15
so... how do i figure that out?

---

### Post by krunge on 2008-10-15
> **schmidtbag said:**
> so... how do i figure that out?

If it is your own NAT router, you can usually configure port forwarding for it via a web browser connecting from the inside.

[http://www.portforward.com/help/portforwarding.htm]("http://www.portforward.com/help/portforwarding.htm")

[http://www.portforward.com/default.htm]("http://www.portforward.com/default.htm")

[http://www.uvnc.com/addons/routerconf.html]("http://www.uvnc.com/addons/routerconf.html")

---

### Post by schmidtbag on 2008-10-16
unfortunately it is not my router, so is there any other choice?

---

### Post by krunge on 2008-10-17
> **schmidtbag said:**
> unfortunately it is not my router, so is there any other choice?

If that router is acting as a firewall and blocking all incoming connections then it is impossible for someone to use a vnc viewer to initiate a connection to you.

However it might not be blocking connections or doing NAT. To determine if the router is really doing NAT do these:

Figure out your internet facing IP address from here: [http://www.whatismyip.com/](http://www.whatismyip.com/)

Figure out your linux machine's IP address by running the /sbin/ifconfig command.

If the linux machine's IP address does not start with 192.168 or 10. have the remote vnc viewer user try to ping that IP address.  Then maybe point their VNC viewer to that IP address.  If you have problems, post both IP addresses here.

If that doesn't work a reverse connection with the '-connect' option might be possible:

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-connect](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-connect)

Another option is an SSH tunnel (-R option) via a machine the remote user can reach. You would need to have a login account on that machine.

More info:

[http://www.karlrunge.com/x11vnc/#firewalls](http://www.karlrunge.com/x11vnc/#firewalls)

[http://www.karlrunge.com/x11vnc/faq.html#faq-reverse-connect](http://www.karlrunge.com/x11vnc/faq.html#faq-reverse-connect)

[http://www.karlrunge.com/x11vnc/faq.html#faq-reverse-connect-proxy](http://www.karlrunge.com/x11vnc/faq.html#faq-reverse-connect-proxy)

[http://www.karlrunge.com/x11vnc/faq.html#faq-firewall-out](http://www.karlrunge.com/x11vnc/faq.html#faq-firewall-out)

---

