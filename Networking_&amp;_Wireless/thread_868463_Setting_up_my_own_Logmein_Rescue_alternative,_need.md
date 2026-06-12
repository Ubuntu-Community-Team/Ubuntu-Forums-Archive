---
title: "Setting up my own Logmein Rescue alternative, need some help"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by biasedopiniondrummer on 2008-07-23
Hey guys I've got an odd question for you and I would love any input at all, you could call this kind of a brainstorming post. Here's my situation

--------
I need to remotely connect to multiple desktop computers running ubuntu 8.04, the computers will all be behind separate routers and I will not have access to the routers to set up port forwarding. The users of the computers I am connecting to lack the technical ability to do anything in the command line.
--------

Here's the solution I'm considering. Set up a VPN that the computer can connect to and then use VNC to view and control the clients computer. there are some stipulations though, 
[LIST]
[*]the client will feel like there privacy is violated if I can remotely  connect to there computer at any time. It must take interaction from Me and the client to establish the connection
[/LIST]
[LIST]
[*]I cannot allow multiple clients to access the same VPN simultaneously because this establishes a security risk if they can share files or remotely access one another
[/LIST]
[LIST]
[*]Due to the lack of knowledge of the clients there requirements must not exceed clicking a few buttons or launchers
[/LIST]

I've considered using Hamachi but would rather set up my own VPN (I don't want to get dependent upon a service that may not always be there), What do i need to do this (Hardware and Software) and how should i configure it? Any ideas are welcome! and please explain well as my networking knowledge is limited. Thanks Guys! Hopefully you can help me solve this puzzle.

---

### Post by biasedopiniondrummer on 2008-07-29
hey guys, any thoughts on this?

---

### Post by jpfreely on 2008-08-28
Perhaps you could have an SSH server of your own accessible from outside. Could run it on port 80 or 443 to ensure it's likely accessible even behind restrictive firewalls.

Then clients would connect with a command like ssh -R 1234:localhost:5900 user@your-server. They'd need to have their VNC turned on but you could do that in a script (I assume, haven't tried that). They'd have to enter the password for 'user'. Maybe you could set a different password each time you connect to someone so that they can't connect again without your assistance.

Then you'd connect to your server at port 1234 with your VNC client, which would show you their PC. Perhaps you could have a unique port for each client if you are likely to have multiple connections going.

I think all of this would be bash scriptable. You could use some zenity to make your bash script pop up UI dialogues.

---

### Post by biasedopiniondrummer on 2008-08-30
interesting idea!  so you are proposing tunneling vnc through ssh? i like the way you think. can you think of any possible problems that we may run into? considering the fact that users can be in multiple different situations as far as internet connection (behind multiple routers and such), also is there going to be much lag in the vnc when tunneling throught ssh? assuming that the custmer has an 4 meg connection.

---

### Post by jpfreely on 2008-08-30
On a 4 meg connection there should be very little lag really. VNC was designed with remote / slow connections in mind and uses compression etc. The upstream connection for the customer will probably be the limiter. I know where I live many people have only 128 kbps upload but VNC is still plenty tolerable.

Using the reverse SSH tunnel should work in most situations, reason being that the customer is actually the one initiating the connection. It's like the way a web browser works I guess - they initiate an outgoing connection on port 80 and then the remote server gains permission to make an incoming connection to send data back. The SSH tunnel should therefore work through any NAT configuration etc.

The only situation it wouldn't work I think is if the customer is behind a proxy for internet access. It is possible to put SSH through a proxy (I do it using a program called ProxyCommand) but it would be difficult to detect the customer's proxy settings and stick them in the right place for the command. Not completely impossible though - most auto config proxys will respond to a request for a document at [http://wpad/wpad.dat](http://wpad/wpad.dat) because this is what Internet Explorer asks for when it is doing auto config. This returns a file with the proxy information. Coding a solution to do that would be a little tricky though.

---

### Post by Saghaulor on 2009-08-13
You'll want to tunnel a VNC connection through SSH anyways because VNC is insecure. Some VNC's offer their own encryption, but many of them do not.

If you tunneled through a VPN with VNC, that would be secure, but it doesn't meet the criteria that you listed.

---

