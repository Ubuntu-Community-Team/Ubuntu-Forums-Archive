---
title: "VNC over SSH, almost there"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2007-05-11
I've followed the [guide]("http://ubuntuforums.org/showthread.php?t=383053") on this forum and I could do the VNC stuff from my XP laptop to my Feisty desktop. Also the SSH connection worked fine on the local LAN. A couple of questions though:

- I couldn't get PuTTY to do VNC over the SSH connection. It says "can't connect" or something (have to check at home for the exact phrasing). With the PuTTY SSH connection, the 127.0.0.1 IP is the localhost of the remote machine, right? So in PuTTY I make a tunnel from port 50000 to 127.0.0.1::5900 which is my VNC port on the other side.
My understanding is that I connect to e.g. port 50000 of my machine (127.0.0.1::50000), to connect to port 50000 of my winXP machine which gets tunneled to port 5900 of the Feisty machine. Why is it not working?

- From work I tried the SSH connection, but the connection times out. I have my router set to port forwarding, and the SSH deamon is running on the Feisty machine. PuTTY even shows the correct IP number on top of the terminal window (does that mean the connection to my router is established?).

Since there's so many services and ports involved, I'm not sure how to find the flaw in my config. Is the port forwarding incorrect? Is my SSH deamon not taking external IP adresses, is my Feisty firewall blocking something? Is my understanding of localhost 127.0.0.1 not correct?

How can I proceed?

---

### Post by DFreeze on 2007-05-16
...anybody...?

---

### Post by bmt on 2007-05-17
I can't help you directly (I'm still trying to get it to work myself), but try posting your question on the end of the HowTo thread that you linked to in your original post.

Edit to add:

I've got a connection working on the LAN.  Regarding your error 'Failed to connect to server ...', it is necessary to log-in to the remote machine at the PuTTY terminal -- use your normal user login name then enter the ssh passphrase at the prompt.  *Then* start the local VNCviewer and you should get the vnc password prompt.

---

### Post by psiu on 2007-05-17
well, I won't be much help I'm afraid, but I think the understanding of the 127.0.0.1 is flawed. That's the internal localhost...what you would need is the computer's IP on the LAN, i.e. 192.168.1.100 or something of the sort. Or possibly the WAN-side IP of the network...arrgggh.

Not that I've got this stuff to work that well, mind you. :P

I can use Putty to connect to my homebrew router via the wan-ip, and also connect to it via vpn and get the lan-ip....but i haven't gotten my vnc to the computers on that lan working yet...plus I have WOL issues to deal with.

But definitely pretty sure that if you tell your computer to connect to 127.0.0.1, *every* computer you are on will treat that as it's internal IP...

---

### Post by bmt on 2007-05-17
You have to make a connection to localhost to enter the ssh tunnel -- 127.0.0.1:50000 is correct, where 50000 is the ssh port.

---

### Post by smooth_b on 2007-05-17
Have you tried NXSERVER? I have recommended this to so many people that I should be a salesman. You can check it out at [http://nomachine.com](http://nomachine.com) 

Here are some screenshots:

[http://www.nomachine.com/screenshot/linux-client.php](http://www.nomachine.com/screenshot/linux-client.php)


This works much better that VNC.

---

### Post by DFreeze on 2007-05-18
> **smooth_b said:**
> Have you tried NXSERVER?

Thanks for your recommendation, I'm gonna try that next for my own linux - linux and windows - linux connections. But the goal of this exercise is that I want to get it to work with VNC for the people I help with their computers. Right now, every trivial fix costs me (part of) an evening just to get there and back. If I can grasp this SSH and VNC thing, I might be able to do it from my own PC, which would save a lot of time.

[ideal mode] 
If I could somehow make a script / batch file on their desktop that, when doubleclicked, automatically connects to my SSH server, and starts listening for VNC traffic on that tunnel. They call, doubleclick, I fix.
[/ideal mode]

---

### Post by ntetreau on 2007-05-18
In my case, when I want to use vnc through ssh, I use this command:

vncviewer -via host.dyndns.org 192.168.1.8:0

the -via switch for vncviewer indicate that vnc will use ssh to connect to the host.dyndns.org.  This address points to my home router or gateway.  After vnc is connected to the gateway through the ssh port, it looks for the computer with the ip adress 192.168.1.8 on my home lan.  vncviewer connects to the x session :0, hop this helps.

Nic

P.S.:  Freenx works very well for me and his much faster, but it creates a new X session, which is not always ideal.

---

### Post by DFreeze on 2007-05-19
My situation is similar, but I've routed the SSH traffic to a specific port in my ADSL modem/router to the computer where sshd is running. So when I connect to my IP (host.dyndns.org), it forwards the SSH traffic there, so the IP number I should give in would be localhost, right? Since I'm already on the right machine.

Anyway, I can't even get it to work yet on my local LAN, so I think I should start there... Then see if the host.dyndns.org points to the correct IP and I can connect to it. After that see if SSH traffic is possible from the outside... Hmm, quite a road to go...

---

### Post by bmt on 2007-05-19
> **DFreeze said:**
> My situation is similar, but I've routed the SSH traffic to a specific port in my ADSL modem/router to the computer where sshd is running. So when I connect to my IP (host.dyndns.org), it forwards the SSH traffic there, so the IP number I should give in would be localhost, right? Since I'm already on the right machine.
No, if you're using port forwarding on the router, you only need to include the public IP (or the dyndns name) and the port number.
> Anyway, I can't even get it to work yet on my local LAN, so I think I should start there... Then see if the host.dyndns.org points to the correct IP and I can connect to it. After that see if SSH traffic is possible from the outside... Hmm, quite a road to go...
You can't test dydns service from within the LAN that dyndns is pointing to.  At best you get the router's internal port and its set-up page.  This can be worrying ('Can the Internet access my router set-up?' :-o), but it's normal.

---

### Post by insane_alien on 2007-05-19
i get the same problem. when i try it over my LAN (modified settings to use the IP rather than dyndns) i get connection refused.

---

### Post by ntetreau on 2007-05-20
When Ï use vncviewer over ssh, I do need to include the -via IP-gateway.  This only tells vncviewer to use the forwarded ssh port on the gateway.  However, vncviewer will complain that it needs the server's IP (which is not the same at that point as the gateway's IP, because you already passed it).  Thus I need to give my home lan's IP as well.  I haven't found a way around it:

vncviewer -via host.dyndns.org serverIP.home.lan:0

Make sure you have the ssh port forwarded.  insane_alien, can you use vncviewer from within you home lan?

Nic

---

### Post by DFreeze on 2007-05-21
Hey ntetreau, thanks for explaining that. Slowly I'm getting my head around these things. The laptop I used to get the SSH tunnel working is a WinXP machine, so the CLI instructions you gave will not help there. I can only type an IP address in uVNC which (I guess) doesn't like a -via option.

I do recall not having given the screen number in uVNC. That didn't stop uVNC from working without SSH, so I guess it should also work without feeding a screen number through the SSH tunnel, right?

I'll experiment some more, when I get home.

---

### Post by ntetreau on 2007-05-22
you are right, it should work without the screen number, good luck

Nic

---

### Post by DFreeze on 2007-05-31
A quick status update: I've got it working on my LAN. Stupid little thing: in PortaPuTTY I have to specify the SSH-tunnel ** and press 'Add' **. Strangely I completely overlooked that button, and thought filling in the ports was all there was to it...

Now to get it to work through my router...

---

