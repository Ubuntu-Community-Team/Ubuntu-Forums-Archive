---
title: "remote desktop linux to windows"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by crhumber on 2007-07-07
Does anyone know how I can access my windows computer via remote desktop from my linux machine?  I searched the forums but didn't find what I was looking for.  Can someone explain how to do this or point me to a thread that explains this?? thanks

---

### Post by tgm4883 on 2007-07-07
Use terminal server client.  

Applications > Internet > Terminal Server Client

Providing that you have enabled remote desktop connection in Windows

---

### Post by ceargle on 2007-07-07
I'm not sure about RDP from linux, but there are a few alternatives.  You may want to look into [http://www.realvnc.com]("http://www.realvnc.com") or [http://www.tightvnc.com]("http://www.tightvnc.com").  They both utilize the VNC protocol, and I've use both with equal success on Windows and Linux desktops. Login passwords, etc are sent in plain-text, so you may want to look into SSH forwarding if you're not in a secure environment.

---

### Post by tgm4883 on 2007-07-07
> **ceargle said:**
> I'm not sure about RDP from linux, but there are a few alternatives.  You may want to look into [http://www.realvnc.com]("http://www.realvnc.com") or [http://www.tightvnc.com]("http://www.tightvnc.com").  They both utilize the VNC protocol, and I've use both with equal success on Windows and Linux desktops. Login passwords, etc are sent in plain-text, so you may want to look into SSH forwarding if you're not in a secure environment.

RDP works fine.

---

### Post by crhumber on 2007-07-08
Can someone please walk me through this a little?  It seems easy, but I keep getting the error "connection refused".  I can ping my windows computer and I can access its shared files using samba, but for some reason I can't connect RDP.  I have accessed remote assistance in windows.  What else do I check?  thanks

---

### Post by Sunforge on 2007-07-08
Remote assistance and Remote Desktop are separate elements within Windows. 
 
Remote assistance is safer as you have to invite someone to remotely control your machine
Remote Desktop means that anyone with an RDP client can attempt to connect to your machine (firewall and the correct username/password permitting).
 
Anyway it's worth checking to ensure that you've got RDP turned on before looking any further into the more interesting problems that can arise.
 
So if you've got RDP set up on your Linux box, go to your Windows machine and:
 
Right click "My Computer"
Select "Properties"
Under "Remote Desktop" Check "Allow computers to connect remotely to this computer"
In the "Select users" option you will note that the administrator is always permitted. If you're the only user of the machine that'll be you. 
 
RDP under Linux isn't as smooth as RDP under Windows but it gets the job done.
 
Depending on the machine you're using (Win 2K, XP SP1 or 2) you may have to check your windows firewall as well. Post SP2 it's on as far as I recall - this may also be a cause of your problems, ditto Zone Alarm and the rest of the software firewall brigade.

---

### Post by tgm4883 on 2007-07-08
What version of windows do you have?  2000?  XP Pro?  XP Home?

---

### Post by crhumber on 2007-07-08
Ahh...I have XP home edition and the remote desktop box isn't there.  This must be the problem.  I know this is a Windows question, but does anyone know if I can add RDP to XP home edition??  Thanks for the help.

---

### Post by tgm4883 on 2007-07-08
You cannot RDP into an XP home edition.  Sorry, you need to pick up a copy of 2000, XP Pro, or any server edition

---

### Post by Norst on 2007-07-08
Remote Desktop connection is not available in XP Home. I think there are a few hacks out there (replacing DLLs and such) that may enable it but I've never tried.

---

### Post by crhumber on 2007-07-08
thanks, thats what i needed to know

---

### Post by quattroman on 2007-07-10
XP Media Center, had remote desktop available, I believe that's next from home

---

### Post by unouroboros on 2007-07-11
I've got an additional question to this topic: 

I want to connect to work using ubuntu (Terminal Service Client).
My work requires Putty (ssh).

I can connect putty to work, but when I try to log in using my credentials through TSC/RDP, it says "Connection Refused". (Again, Putty DOES connect. RDP does NOT)

Any help would be appreciated as to reasons this might be happening.

Helpful Information:
1) I'm using a router. 
2) I have an XP and ubuntu machine both using this router. 
3) I can connect to work with the XP machine
4) I can RDP from linux to my XP machine.

Thanks.

---

### Post by tgm4883 on 2007-07-11
> **unouroboros said:**
> I've got an additional question to this topic: 

I want to connect to work using ubuntu (Terminal Service Client).
My work requires Putty (ssh).

I can connect putty to work, but when I try to log in using my credentials through TSC/RDP, it says "Connection Refused". (Again, Putty DOES connect. RDP does NOT)

Any help would be appreciated as to reasons this might be happening.

Helpful Information:
1) I'm using a router. 
2) I have an XP and ubuntu machine both using this router. 
3) I can connect to work with the XP machine
4) I can RDP from linux to my XP machine.

Thanks.

You have to tunnel your Terminal Service Client through the SSH.

A quick google turned up this
[http://wiki.bath.ac.uk/display/Linux/HOWTO+Use+Remote+Desktop+from+Linux](http://wiki.bath.ac.uk/display/Linux/HOWTO+Use+Remote+Desktop+from+Linux)
Which is written for a school on how to connect to their network, but it should be adaptable by just changing the address.  As an added bonus, it uses Ubuntu :)

---

### Post by unouroboros on 2007-07-11
Thanks!
I'll try it out.

> **tgm4883 said:**
> You have to tunnel your Terminal Service Client through the SSH.

A quick google turned up this
[http://wiki.bath.ac.uk/display/Linux/HOWTO+Use+Remote+Desktop+from+Linux](http://wiki.bath.ac.uk/display/Linux/HOWTO+Use+Remote+Desktop+from+Linux)
Which is written for a school on how to connect to their network, but it should be adaptable by just changing the address.  As an added bonus, it uses Ubuntu :)

---

### Post by unouroboros on 2007-07-12
Couldn't get it to work. 

Doesn't putty make an ssh tunnel? That connects - ssh. 

Any other suggestions for why RDP not working?

---

### Post by netreg on 2007-07-12
If you want to connect to a win XP home box from linux then simply use vnc.   Install vnc on your winxp and then you can use the terminal server in ubuntu to connect, making sure you change the protocol from RDP to VNC.

regards :)

---

### Post by unouroboros on 2007-07-12
> **netreg said:**
> If you want to connect to a win XP home box from linux then simply use vnc.   Install vnc on your winxp and then you can use the terminal server in ubuntu to connect, making sure you change the protocol from RDP to VNC.

regards :)

Thanks for the reply.

However, I want to connect to my work (XP Pro) - requiring Putty SSH tunnel. 
Is this some setting that the IT department needs to deal with? (I'm stumped because I *can *connect using RDP from my XP machine to the work network using Putty)

Any other suggestions?

---

### Post by unouroboros on 2007-07-12
My previous post may be ambiguous. 
I *can* connect to my work network using Putty (SSH) - which I need to do.
I *can* connect to work using Putty and RDP from XP machine
I *can* connect to work using Putty using Ubuntu.
I *cannot* connect to work with RDP using Ubuntu - after connecting with Putty SSH tunnel.

Hope that clarifies.

---

### Post by joshov on 2007-07-12
I've got a question along these lines, I've been reading and kind of know, but just want to be clear.

I want to log into my Ubuntu machine from my XP home machine.

Do I use putty/ssh to sign in username/password . . ? (not sure about)

Then any Vnc to remote and control (which I can, know how, and have done)

Both/all computer on the same network.  Hooked to 1 (one) wireless router.

Thanks.

---

### Post by perarild on 2007-07-31
I have almost the same problem as you unouroboros, although I'm connecting to my own server (Windows), not one at work.

I tried to follow the instructions in the document linked to by tgm4883, and I managed to get a ssh tunnel working, but I was not able to connect to the server using rdp (Terminal Server Client) through the tunnel.

However by opening port 3389 (Which is the default rdp port) on the router that my server is behind I managed to connect, also this THROUGH the tunnel. This I know because if I stop the tunnel established to the server while rdp is connected, also the rdp connection is lost.

I know this doesn't solve your problem (or mine), I just don't know why port 3389 has to be open, as the connection is tunneled through port 22, and thought I would share my experiences.

Anyone have any thoughts on this?

Thanks for any replies

---

