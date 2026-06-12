---
title: "[SOLVED] SSH Tunneling VNC"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by xc3ll on 2008-08-05
Ok, I've searched this everywhere, and I've found a few guides, but most of them deal with using Windows for one machine and another on this site used reverse tunneling.  Coupled with the fact that I still have a hard time wrapping my head around this, I'd figure I'd ask here and see if I'm on the right track.  Here's my situation:

3 Machines:
ME
INTERMEDIATE
VNCSERVER

I would like to vnc from ME to VNCSERVER.  The only problem is that I can't access VNCSERVER.  I can however, access VNCSERVER through INTERMEDIATE.

So far what I've been doing is:

ME -> ssh -> INTERMEDIATE -> ssh ->VNCSERVER


To help you out, this is what my term looks like:

ME $ ssh INTERMEDIATE
INTERMEDIATE $ ssh VNCSERVER
VNCSERVER $ echo I'm here!

So, I've been trying to tunnel from ME to VNCSERVER but I can't figure it out.  Do I have to tunnel 2x?

I'm thinking I have to do this:
INTERMEDIATE $ ssh -NL 1234:localhost:5901 VNCSERVER

and then
ME $ ssh -NL 5901:localhost:1234 INTERMEDIATE
ME $ vncviewer localhost:1

Is that right? I would try it out, except I'm afraid that I'll screw something up.  Normally, I'd do it anyways, but the INTERMEDIATE box isn't mine and is used by a bunch of other people.

Thanks for your help!

**EDIT:** Ok, after doing a bunch of searching, I've found that this should work:

ME $ ssh -N -L 5903:VNCSERVER:5901 username@INTERMEDIATE
ME $ vncviewer:3 <- done in a seperate xterm

But, I get this error from ssh:
channel 2: open failed: connect failed: Connection refused
and vncviewer does not connect.

Any help?

EDIT 2: Added -vv, here's the full error message:

debug1: Connection to port 5903 forwarding to VNCSERVER port 5901 requested.
debug2: fd 6 setting TCP_NODELAY
debug2: fd 6 setting O_NONBLOCK
debug1: channel 2: new [direct-tcpip]
channel 2: open failed: connect failed: Connection refused
debug1: channel 2: free: direct-tcpip: listening port 5903 for VNCSERVER port 5901, connect from 127.0.0.1 port 53002, nchannels 3

---

### Post by xc3ll on 2008-08-06
Oh snap. I just solved my problem.

I woke up today and had an epiphany.  Why not try pinging my box from the remote box?  So, I ssh'ed to the VNCSERVER box and pinged my box.  Hallelujah! It works! So I then created a reverse tunnel, and boom! VNC works!!! WOOOO HOOOO!!

I'll add a solved to this post.  I hope this helps someone else out one day.  

Here's the command I used:

VNCSERVER $ ssh -N -R 5901:localhost:5901 ME

where ME is the computer you want to run vncviewer on.

Then just:

ME $ vncviewer localhost:1

Man, I wanna sing the Weezer song "The Greatest Man That Ever Lived"

[I]
I ammm the greatest man that ever lived... I was born to give... I ammm the greatest man that ever lived.... RADIOACTIVE!!!![/I]

---

