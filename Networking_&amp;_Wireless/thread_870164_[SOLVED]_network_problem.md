---
title: "[SOLVED] network problem"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by jonderson on 2008-07-25
I am trying to access my ubuntu desktop at work from my home. 
I have in the office dsl run first through a router and from there a windows xp computer and computer running ubuntu. from inside of the network I am able to connect to the ubuntu desktop from the xp computer without a problem. My issue comes with trying to get access from outside the LAN. 

From Home I can go directly and get acces to my router but am having trouble getting to the computers. I have turned on port forwarding at the router for port 5900 and 5800 to be sent to the ubuntu computer. I am tying to connect via SSh and have used PuTTY with the following config:

Hostname/IP XX.XX.XX.XX port 22 under SSH tunnel I have put 

sourceport 5900
destination :  192.168.0.2:5900

I am lost now. Any help would be greatly appriciated.

---

### Post by Jimbro727 on 2008-07-25
> **jonderson said:**
> I am trying to access my ubuntu desktop at work from my home. 
I have in the office dsl run first through a router and from there a windows xp computer and computer running ubuntu. from inside of the network I am able to connect to the ubuntu desktop from the xp computer without a problem. My issue comes with trying to get access from outside the LAN. 

From Home I can go directly and get acces to my router but am having trouble getting to the computers. I have turned on port forwarding at the router for port 5900 and 5800 to be sent to the ubuntu computer. I am tying to connect via SSh and have used PuTTY with the following config:

Hostname/IP XX.XX.XX.XX port 22 under SSH tunnel I have put 

sourceport 5900
destination :  192.168.0.2:5900

I am lost now. Any help would be greatly appriciated.

Is your SSH server running on the default port, 22?  If so, forward whatever port you'd like to port 22, if your router supports that (most routers support this with a firmware upgrade, if not out of the box).  So you would forward port 5900 to port 22 on your Ubuntu box (using its local IP).  Tell PuTTY to connect to your office's external IP address at port 5900, your router will forward that to your Ubuntu box on port 22, and you should be all set.  

The other option is to change the port that the SSH server listens on to 5900.  In your router config, forward port 5900 to your Ubuntu box, port 5900.  Then from your local network, you'll ssh using port 5900, and from outside of your LAN you'll also connect using port 5900, except you'll use your external IP address versus your local IP.

---

### Post by jonderson on 2008-07-26
Sorry,I am completely new to trying to do all of this stuff. I am trying to do a remote desktop connection to this computer so I have access to my files from home. 

Does my Ubuntu desktop also need to be running something else. You mentioned SSH server? I am lost. I guess I am just missing something?? Sorry for the ignorance. I know that inside the LAN this works but Why am I not able to reach from outside. I have tried the info I put in the above post with PuTTY. 
(Inside the LAN I am using VNC Viewer and connecting to 192.168.0.2:5900). 

I will post all of the info I know here except my IP address If anyone can take a look and see what I am doing wrong that would be greatly appriciated. Again I AM able to use VNC from my windows desktop inside the network to the Ubuntu machine but I am not able to get anything from outside of the network (home) It just tells me connection refused.

I have an ACtiontec router 
static IP - rfc1483 bridged
lan address of 192.168.0.1
has static dns Servers listed
remote management is on
on port forwarding option I have
PPTP port 1723 and 
VNC ports 5800 and 5900
forwarded to my ubuntu machine at IP addres 192.168.0.2

If I am needing to install the OpenSSHserver just let me know. I can walk myself through that, but may just need a little bit of help on how to open ports once that program is installed. 

Thanks againg for any help!

---

