---
title: "remote desktop"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2006-11-09
I need to connect with a Remote Desktop to 50 pc with edgy we have given to our salesmen, but cannot open a port in every of those 50 routers. Is there any way to remotely connect without changing the dsl router specs.?
Thanks!

---

### Post by geoffm33 on 2006-11-09
Without opening the ports and forwarding to the PC, I'm not sure how you could.

You could get a VPN appliance at the central office and setup a point to point VPN. This is the safest way anyhow, but more complicated than port forwarding.

---

### Post by dbott67 on 2006-11-09
You can open the appropriate ports on your router and use 'reverse VNC'.

In a nutshell, you need to install VNC on each computer and they would use the 'vncconnect' command to connect to your computer which is running 'vncviewer' in 'listen mode'.

[http://www.realvnc.com/products/free/3.3.7/man/vncconnect.html](http://www.realvnc.com/products/free/3.3.7/man/vncconnect.html)

-Dave

---

### Post by jmvidalvia on 2006-11-09
Great ideas! both.
I'll try.

---

### Post by dbott67 on 2006-11-09
> **dbott67 said:**
> You can open the appropriate ports on your router and use 'reverse VNC'.

In a nutshell, you need to install VNC on each computer and they would use the 'vncconnect' command to connect to your computer which is running 'vncviewer' in 'listen mode'.

[http://www.realvnc.com/products/free/3.3.7/man/vncconnect.html](http://www.realvnc.com/products/free/3.3.7/man/vncconnect.html)

-Dave

To further expand on my post (for others that may cross this path in the future), most home routers do not block outbound traffic; they only block unsolicited inbound traffic.  By getting the user to initiate a 'reverse VNC' connection, they are in fact soliciting the traffic.  This means that you are able to connect to their computer without having to forward any ports on their router.  The only caveat is that you must forward port 5500 on ***your*** router to ***your*** computer so that it can receive the 'reverse VNC' call.

-Dave

---

### Post by jmvidalvia on 2006-11-09
Thanks for your help.
I installed Xvncviewer and vncserver.
To make everything clear (server and client is a little bit confusing as we are in reverse mode) I amb the boss and want to see my salesman pc. My ip is 111.222.333.444 and my port 5500 is open to my computer
I must type:
vncviewer -listen
He must type:
vncconnect -display ????????????????
(here is were I get some confussion: **which would be the command line?**)
Many thanks in advanced!

---

### Post by dbott67 on 2006-11-09
You're on the right track.  I'll provide specific examples with respect to IP addresses & commands, you can modify them to your situation:

**Your Computer Internal IP:** 192.168.0.100
From the command line on your computer type:
```
vncviewer -listen
```

Your Router Internal IP: 192.168.0.1
Your Router External IP: 111.222.333.444
Port Forward Rule: TCP 5500 --> 192.168.0.100
[B][U]
Salesman PC (at remote site behind router)[/U][/B]
Internal IP: 192.168.1.100
From the command line type:
```
vncconnect 111.222.333.444:5500
```
if that doesn't work, try:
```
vncconnect -display 0 111.222.333.444:5500
```

If YOUR external IP (111.222.333.444) is dynamic, most routers can use Dynamic DNS ([www.dyndns.org](www.dyndns.org), [www.no-ip.com](www.no-ip.com), etc.) to provide a static FQDN to a dynamic address.  The basic service is FREE. So, rather than them always having to find out your IP address, you could write a little shell script:
```
#!/bin/bash
vncconnect -display 0 **[COLOR="Red"]jmvidalvia[/COLOR]**.dyndns.org:5500

```

**[COLOR="Red"]jmvidalvia[/COLOR]** would be the 'hostname' you create at dyndns.org.  There is a setting in most routers that would allow you to enter your dyndns.org account information to keep the IP address up-to-date.

I use this method to remote home and connect to my various computers.

-Dave

---

### Post by jmvidalvia on 2006-11-10
Fortunately I have static IP: it makes everything much simpler.
Anyhow, your dynamic solutions seems easy and really usefull for other people.
Your solution with vncconnect is really great and quite simple.
Thank you very much!!

---

### Post by jmvidalvia on 2006-11-10
I am trying this system within our LAN in order to check everything is ok but it doesn't work. Is this normal?, I mean, will it work outside although it doesn't work locally.
I opened port 5500 to my pc (1st pc)
In 1sr pc I write
vncviewer -listen
and it keeps waiting.
In 2nd pc I have tryied everything:
vncconnect IP:5500
In IP I wrote the local ip of the router, the local ip of the other machine,  the public ip of the router, and nothing happens.
I also add -display 0
I tryied with and without :5500 
All combinations.
I hope the reason is I amb trying it within the same LAN.
Thank you!

---

### Post by dbott67 on 2006-11-10
It depends on how you are trying to connect on the LAN.

The command 'vncviewer -listen' will keep the window open, if you want to send the command to the background (so you can close the terminal window), you would need to add a '&' to the end of the command:
```
vncviewer -listen&
```
Close the window, open a new window and type:
```
ps aux | grep vncviewer
```
to verify the process is still running.

For local connections, you would run 'vncviewer -listen' on your computer, and they would type:
```
vncconnect 192.168.0.100:5500
```
The IP would have to be the local IP, not the public internet IP.

Also, I think that you may have to go under SYSTEM > PREFERENCES > REMOTE DESKTOP and enable it on the SALESMAN PC.

I was able to get it working on my home computers using this method... so we're close.

-Dave

---

### Post by jmvidalvia on 2006-11-10
Dave, thank you very much for your help.
I feel so sad...: I'm sure I did everything, but it doesn' work.
1st PC is listening for sure
5500 port is open
Both have enabled remote desktop in sistem settings
but when I type in 2nd pc...
vncconnect 192.168.1.128:5500 
simply nothing happens.
(note: vncserver and vncviewer work ok in both machines, in both directions)
Any last idea about what can be happening?
Many thanks again!

---

### Post by dbott67 on 2006-11-10
I just tested a reverse connection from work to home and it worked.  Basically, I did a regular VNC connection home, ran 'vncviewer -listen' and then used my Windows XP computer at work to make a connection.  Everything worked as it should --- my work desktop appeared on my home computer.

So, if you've got some patience I'm sure we can work through it.

-Dave

---

### Post by jmvidalvia on 2006-11-11
Is it posible I have a firewall activated? Can this be blocking income signal through port 5500?
I installed standard Edgy.
Thank you very much.

---

### Post by dbott67 on 2006-11-11
The command to view if iptables (the base system for most firewalls in Linux) is iptables -L:
```
dbott@edgy:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```
Mine is not enablesd (i.e. there are no rules).

-Dave

---

### Post by jmvidalvia on 2006-11-11
Mine looks same as yours, so I must have firewall disabled too.
I will keep on trying..
Thank you very much

---

### Post by dbott67 on 2006-11-13
Hi jmvidalvia,

I've got it...  I had some computer troubles over the weekend & I had to re-install my desktop --- I decided to give edgey a try.  Anyhow, I've figured out what the problem is:

On the "remote" computer (the one that you want to control), you need to install the x11vnc package:
```
sudo apt-get install x11vnc
```
Once installed, the remote user needs to issue the following command:
```
x11vnc -connect your.computer.ip.address:5500
```

Before they can "send their desktop", you need to set vncviewer to listen-mode:
```
vncviewer -listen
```

Hope this works for you... I've just tested it on 2 laptops to connect to my home PC & it works!  Attached is a screenshot of my desktop showing the 2 remote laptops (VNC:Tecra & VNC:Dapper).

-Dave

---

### Post by jmvidalvia on 2006-11-14
Hi Dave!
I knew you were going to get the solution!
It works great. You can not imagine how much your helped me.
If your are thinking about comming to Barcelona, just tell me: I can not offer you technical assistance, but a bootle of good wine!
Thanks a lot.

---

