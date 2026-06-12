---
title: "ssh issue"
date: 2014-05-07
forum: Networking &amp; Wireless
---

### Post by evaristegalois on 2014-05-07
I want to leave an old computer with ubuntu installed running at home to log into from work (where everything is windows).

I opened a port on my router (call it XXXX, a number somewhere between 1000 and 9999) and forwarded it to the appropriate internal IP address 192.168.0.XX (let this be INTIP, whereas my IP address for the rest of the world is OUTIP; also let the IP address of my webhosting service be called WEBIP).

From another desktop on the same router, both

ssh -l username INTIP

and

ssh -l username -p XXXX OUTIP

work fine.

I can also ssh into my webhoster's unix system

ssh -l webusername WEBIP

and run

ssh -l username -p XXXX OUTIP

from there, and that works fine as well. From my Windows computer at work, I can also run

ssh -l webusername WEBIP

and get to my webhoster's unix system. BUT when I run

ssh -l username -p XXXX OUTIP directly from my Windows computer at work, I get

ssh: connect to host OUTIP port XXXX: Connection refused

I guess my Windows computer refuses to connect to a port other than 22? Can I work around this, or must I open up port 22 on my computer at home?

---

### Post by ian-weisser on 2014-05-09
Seems like you must open up port XXXX on your router.

Your internal LAN test seems to show that your Ubuntu system is configured correctly to receive the connection, and that the router's port forwarding is configured properly.

---

### Post by tomearp on 2014-05-10
It doesn't sound like port forwarding on the home router is the issue as the home server can be accessed fine via the web hosting server.

You say the Windows machine is on your work network. Is this a network you control? If not, it might indicate that outbound traffic is being restricted.

Presumably you connect to your web host's server on port 22? 
If so you could test for outbound filtering by doing the following from the Windows machine:

Connect to your web host's server. 
Then connect to your home server via the web host server, also [creating a tunnel]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding") that will allow you to access your home router's web interface.
Edit /etc/ssh/sshd_config on the home server to listen on port 22 as well the other port (add a line that says Port 22 underneath the other port declaration).
Restart ssh on the home server (sudo service ssh restart).
Configure your home router to forward port 22 to the home server.
Try and connect to your home server directly from the Windows machine on port 22.

If that works then it strongly indicates that outbound traffic is being restricted based on the destination port. In which case you will need to talk nicely to whoever controls your work network to allow you to make connections to the other port.

---

### Post by spynappels on 2014-05-11
A couple of questions:

How are you running SSH from your Windows computer? Cygwin or PuTTY? Sounds like Cygwin but it would be nice to be sure.

If Cygwin, have you tried PuTTY?

Can you telnet from the Windows machine to port XXXX on EXTIP? If the port is forwarded correctly, you should at least get an ID string of the OpenSSH server on your Ubuntu machine.

The connection refused error is normally either firewall related or port related.

If all else fails, you could try taking network snoops/traces on the Windows machine and on the Ubuntu machine, that would at least tell you if the packets were getting to the Ubuntu machine or not and that they were leaving the Windows machine. If the router supports port mirroring, you could also verify if the TCP packets are getting to the router.

Regards,
Stefan

---

