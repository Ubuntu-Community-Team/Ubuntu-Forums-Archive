---
title: "Understanding Remote Access"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by flowersrj on 2007-12-11
Hi,

First, a couple of questions I have...

1)  If I use SSH & VNC to access a Ubuntu machine, am I creating a different session if someone is already on the target machine or sharing theirs?  And, do I have a choice?

2)  If the answer to the above question is that I am sharing the current logon then what happens if no one is logged on the target machine?

3) If vncserver is started, should I see vncserver on the screen if I do a

      ps aux | grep vnc

Thanks,
Rich

---

### Post by Original Brownster on 2007-12-12
> 1) If I use SSH & VNC to access a Ubuntu machine, am I creating a different session if someone is already on the target machine or sharing theirs? And, do I have a choice?

2) If the answer to the above question is that I am sharing the current logon then what happens if no one is logged on the target machine?

3) If vncserver is started, should I see vncserver on the screen if I do a

ps aux | grep vnc

1. no, to clarify you can only connect using your client to a server that is running so you cannot create a new vncserver session with a client, you just connect to one that is already running.

if 'foo' is your linux box you want to connect to, and 'bar' is the client that wants to view it:
you start a vncserver on 'foo' by default this is screen 1 not 0, which is where the normal desktop is viewed. you cannot start the vncserver on screen 0 and 'share' the login as per windows vnc.
when 'bar' connects on screen 1 you see a grey session with nothing running so you bypass the normal kdm/gdm login prompt.
You can however use x11vnc instead that will allow you to run vncserver on screen 0 follow [this link]("http://www.karlrunge.com/x11vnc/") for info on it.
This I believe shares screen 0 so therefore you will see apps etc running as per the normal user session.
2. see answer above.

3. yes you'll see a process running on the server the name dependant on what server variant you run.

HTH

---

