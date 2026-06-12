---
title: "vpn and vnc"
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by fezzik on 2005-12-05
I have been trying to get into my work computer using vnc.  I tried and it said something about it could be firewall.  I know others that use vpn to get into vnc on windows.  I have the vpn working.  I can get into the company network through vpn.  I can get into my other home computer with vnc.  Now when I use it it says it authenticates but the window never comes up.  Help me please.  So far there hasn't been anything that time and perserverance and this forum haven't solved for me with my transition to Linux.  I just keep digging into more and more complicated stuff or stuff fewer and fewer people do.  Someone has gotten this working or has theories I am sure.  Help a struggling n00b.

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=fezzik]I have been trying to get into my work computer using vnc.  I tried and it said something about it could be firewall.  I know others that use vpn to get into vnc on windows.  I have the vpn working.  I can get into the company network through vpn.  I can get into my other home computer with vnc.  Now when I use it it says it authenticates but the window never comes up.  Help me please.  So far there hasn't been anything that time and perserverance and this forum haven't solved for me with my transition to Linux.  I just keep digging into more and more complicated stuff or stuff fewer and fewer people do.  Someone has gotten this working or has theories I am sure.  Help a struggling n00b.[/QUOTE]
What is the OS and VNC server for the work computer?
What is the OS and VNC client for the home computer?
What port do you have the VNC server set to listen on?

---

### Post by fezzik on 2005-12-06
Server is TightVNC running on a Windows 2000 Professional
Client is vncviewer running on Ubuntu 5.10 Breezy - 686
Best I can tell it is set to use Auto on Ports but in the shaded area that isn't checked it has 5900 and 5800.  

Also I used two other VNC viewers last night one with a graphic interface that had to have the display setting after the ip and the only one that got me to the password was :0.  The others said no such server running. 

With out the VPN (which I am using PPTPConfig by the way) it did nothing but with it I get as far as it asking for my pasword but it says something about successful authentication and says something like it is starting the viewing window but nothing comes up.

Maybe this has something to do with having it set to tunnel all traffic through the VPN.  Just a thought that popped into my head.  I may have to try messing with those settings tonight.  But I am thinking if I set it differently it may not work at all.  Too bad I am at work and my computer is at home grr.  I should bring it with me and mess with it at lunch.  But I have had trouble with stuff working here that doesn't work at home cause it is doing things from the inside which is much different than doing the same thing from outside our network.

On Windows what they do is use the VPN to get into our intranet system then they use VNC or tightvnc on both sides to connect.

I have gotten VPN to work.  Also I have gotten VNC to work on my other computer but not together.  I hope you can help with this extra info.

---

### Post by cwaldbieser on 2005-12-06
[QUOTE=fezzik]Server is TightVNC running on a Windows 2000 Professional
Client is vncviewer running on Ubuntu 5.10 Breezy - 686
Best I can tell it is set to use Auto on Ports but in the shaded area that isn't checked it has 5900 and 5800.  

Also I used two other VNC viewers last night one with a graphic interface that had to have the display setting after the ip and the only one that got me to the password was :0.  The others said no such server running. 

With out the VPN (which I am using PPTPConfig by the way) it did nothing but with it I get as far as it asking for my pasword but it says something about successful authentication and says something like it is starting the viewing window but nothing comes up.

Maybe this has something to do with having it set to tunnel all traffic through the VPN.  Just a thought that popped into my head.  I may have to try messing with those settings tonight.  But I am thinking if I set it differently it may not work at all.  Too bad I am at work and my computer is at home grr.  I should bring it with me and mess with it at lunch.  But I have had trouble with stuff working here that doesn't work at home cause it is doing things from the inside which is much different than doing the same thing from outside our network.

On Windows what they do is use the VPN to get into our intranet system then they use VNC or tightvnc on both sides to connect.

I have gotten VPN to work.  Also I have gotten VNC to work on my other computer but not together.  I hope you can help with this extra info.[/QUOTE]

Can you browse a web page on your Win2K machine over your VPN?  Because if you can, the TightVNC server runs a web server on port 5800+display #.  So you should be able to open up your browser and point it to:
[http://server-ip-address:5801](http://server-ip-address:5801)
This requires Java, but it should work.

If you want to use the normal vncviewer, I have founf that I need to connect to display 1 on Windows.
```

$ vncviewer ${SERVER_ADDR}:1

```

---

### Post by fezzik on 2005-12-07
The Win2K machine is the one at work.  I use Ubuntu at Home.  I haven't tried setting my win2k machine to do a vpn.  It is already inside the company network.  The display 1 doesn't work it has to be set to 0 in order to connect for some reason.  I was going to post the outcome last night of what vnc said but I couldn't so I will have to try again tonight.  It seems to connect everything fine but won't bring up a window so I can control everything.  I will post tonight to show what it is doing.  I will also check the Windows machine to see if I have any settings that may help me get in or something.

---

### Post by cwaldbieser on 2005-12-07
[QUOTE=fezzik]The Win2K machine is the one at work.  I use Ubuntu at Home.  I haven't tried setting my win2k machine to do a vpn.  It is already inside the company network.  The display 1 doesn't work it has to be set to 0 in order to connect for some reason.  I was going to post the outcome last night of what vnc said but I couldn't so I will have to try again tonight.  It seems to connect everything fine but won't bring up a window so I can control everything.  I will post tonight to show what it is doing.  I will also check the Windows machine to see if I have any settings that may help me get in or something.[/QUOTE]
You have virtually the same setup that I do.
At home, I have Ubuntu as the VNC client.
At work I have Win2k.
I vpn into the network at work.
I can vnc in, but I have to use display 1.  I am using TightVNC Server version 1.2.9 (from the about box).  I am using VNC viewer version 3.3.7 on the client.

I guess your firewall could be part of the problem-- you could try telnetting to the prot or something to see if the prot is open.

---

### Post by fezzik on 2005-12-07
Ok I have changed the VNC server to use display 1. Which changed all the ports to 5901 and 5801.  I will give that a try tonight.  It may be a firewall problem but I just figured that was what the vpn was for.  Maybe my VPN account settings don't have permissions for port 5900 or 5800.  That would stink.  I don't know if they have different firewall permissions for different accounts or how that works.  I guess we will check.  Thanks for your help.  I will let you know how it goes.

---

### Post by fezzik on 2005-12-08
Tried display 1 and here is what it gave me.

VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.3 (viewer 3.3)
Password:
VNC authentication succeeded
ReadFromRFBServer: rdr::EndOfStream

but no controller comes up.

---

