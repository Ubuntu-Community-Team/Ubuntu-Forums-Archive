---
title: "[SOLVED] Any vnc experts able to help out a networking noob?"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by FokkerCharlie on 2008-11-18
Hi!

I would like to get vnc up and running here, with a view to assisting a family member with his Ubuntu setup, but am having some problems.

I have actually been trying to connect to my own machine, and in this way test both 'ends' of my setup.  This technique worked a while back, when running Hardy, and of course, created a feedback loop, where I can see the client computer open the window viewing the server (same pc), and so on.  Of course, this is ugly, but it works to prove the system to a certain extent.

Anyway, this hasn't been working.  At the moment, I get this:

```
pc-name:~$ vncviewer xx.xx.xx.xxx  <my ip address for today!>

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Tue Nov 18 22:24:32 2008
 main:        unable to connect to host: Connection refused (111)
```

Same results appending :0 or :5900 to the ip.

Vinagre reports:
Connection to host "xx.xx.xx.xxx:5900" was closed.

And also, trying the vnc server test page ([http://www.realvnc.com/cgi-bin/nettest.cgi]("http://www.realvnc.com/cgi-bin/nettest.cgi") gives me:

```
The IP address requesting this web page is xx.xx.xx.xxx (REMOTE_ADDR)

Connecting to port 5900 ... succeeded.

Waiting for server to send version string... failed: (111, 'Connection refused') 
```

I have firestarter installed, with port 5900 allowed for 'everyone' under 'Inbound traffic policy'.  I have also forwarded port 5900 on my router like so:

```

App   External Packet 	Internal Host 	
     IP Address Protocol Port 	IP Address 	Port
Deluge 	ALL 	TCP 	49152 	79.66.110.136 	49152 	
VNC 	ALL 	TCP 	5900 	192.168.1.102 	5900 	
VNC 	ALL 	UDP 	5900 	192.168.1.102 	5900
``` 	

Where 192.168.1.102 is my local ip address.

Trying vncviewer with that local address, or with my computer name (with and without :0 at the end!) produces the same 'Connection refuesed (111)' result.

I have also checked (and unchecked, and checked again!) the settings in System > Prefs > Remote Desktop:  Allow others to view, and ask for confirmation.

So, what have I missed?  It's driving me nuts!  I have been using Ubuntu for about 1 year, and am getting the hang of it, but am not a networks expert.

All your help appreciated.

Charlie

---

### Post by spiderbatdad on 2008-11-18
Offhand I would say the server is not actually running.```
ps aux | grep vino
```maybe start the server manually:
```
/usr/lib/vino/vino-server
```

---

### Post by Jose Catre-Vandis on 2008-11-18
Are you sure you are running a vncserver on your own machine (for this test) ??

---

### Post by FokkerCharlie on 2008-11-18
Ah-ha!

```
:~$ ps aux | grep vino
charlie   8020  0.0  0.0   3240   804 pts/1    R+   23:20   0:00 grep vino
```
(for interest)

And /usr/lib/vino/vino-server seems to have made quite a difference!  My own computer (and the feedback loop that I was expecting) shows up in Vinagre - *but only on my local domain*.  Previously, I had been trying to run vncserver, and vnc4server.  After running vino-server:

```
~$ ps aux | grep vino
charlie   8575  0.5  0.4  65028  9960 ?        S    23:26   0:01 /usr/lib/vino/vino-server
charlie   9074  0.0  0.0   3240   808 pts/1    R+   23:31   0:00 grep vino
```

if you're interested!

A couple of other things:

The VNC network test page now shows:

```
The IP address requesting this web page is xx.xx.xx.xxx (REMOTE_ADDR)

Connecting to port 5900 ... succeeded.

Waiting for server to send version string...

Unknown server (RFB 003.007) 
```

Which is an improvement on what we had before, and looks like it should work out.

I am having difficulty connecting to my computer via the external ip- I still see the 'Connection to host "79.74.26.213:5900" was closed.' message.  I can ping this IP without a problem.

Am I missing something else?

Many thanks to you for your input so far!

Charlie

---

### Post by spiderbatdad on 2008-11-18
try connecting to [email]machine_ip@external_ip ...of[/email] course the router must be forwarding requests. On a local network it is simply host@machine.

---

### Post by FokkerCharlie on 2008-11-18
Hmm.  That didn't seem to work.

I tried:

Internal IP @ external IP (192.168.1.102@79.74.26.xxx)
and the other way around, and
my computer-name@external IP.

externalip:99, externalip:0, 1 and 2, in vinagre, all reported 'Connection closed' as above.

Regarding the router forwarding requests, I think I have covered that with my port forwarding- or am I labouring under a misapprehension?

Cheers again for your input- I am pleased to be making progress!

Charlie

---

### Post by spiderbatdad on 2008-11-18
ok this works for me...where my machine name is bill-laptop

connect to: ```
 bill-laptop:192.168.1.102@68.114....
```

---

### Post by FokkerCharlie on 2008-11-18
Awwww.  Nuts.

That still doesn't work for me.  I am getting this:

Connection to host "charlie-5920G:6092" was closed.

Goodness knows where the 6092 is coming from.  That port is now open in Firestarter, and forwarded in my router settings.

I am typing:

charlie-5920G:192.168.1.99@79.66.xx.xx in the connect dialog.

Grrrrrr.

Maybe I'll sleep on it and come back tomorrow.  If you have any more thoughts, I'd love to hear them!

Cheerio!
Charlie

---

### Post by FokkerCharlie on 2008-11-18
Ooooooooo!

Just as I thought it wasn't going to work, here's what works for me:

computer-name::port@local-ip@wan-ip in the connect dialog.

eg:

charlie-5920G::5900@79.66.xx.xx

Can go to bed happy now!

VMT for the assistance, much appreciated.

Charlie

---

### Post by spiderbatdad on 2008-11-18
check your machine name...what do you see in the terminal prompt?
charlie@charlie-laptop?

In that case you would connect to charlie-laptop:internal_ip@external_ip

Good luck...should work. Are you running Hardy? There was a bug IDK if they ever fixed it. I am running 8.10

---

### Post by spiderbatdad on 2008-11-18
> **FokkerCharlie said:**
> Ooooooooo!

Just as I thought it wasn't going to work, here's what works for me:

computer-name::port@local-ip@wan-ip in the connect dialog.

eg:

charlie-5920G::5900@79.66.xx.xx

Can go to bed happy now!

VMT for the assistance, much appreciated.

Charlie

\o/  \o/  \o/

---

### Post by FokkerCharlie on 2008-11-19
Hmmm.

Not so sure that this was the solution after all.  If I substitute a fake ip address for my external ip, then it still connects to myself.  Oh, dear.

Not to worry, maybe I'll figure it out, maybe not!

Charlie

---

