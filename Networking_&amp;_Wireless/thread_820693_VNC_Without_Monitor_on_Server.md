---
title: "VNC Without Monitor on Server"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by Oysterville on 2008-06-06
Hey gang,

It's probably an easy fix, but the Great Googly Woogly isn't helping much right now.  I can connect to my VNC server just fine if it has a monitor attached, but if it boots without the monitor it gives me a "vncviewer: ConnectToTcpAddr: connect: Connection refused".  

Is there a way to fix this problem.  Given where I'm putting it I'd rather not need a monitor attached.

Thanks for reading, and any help you can provide.

---

### Post by superprash2003 on 2008-06-06
i saw a similar problem few backs back here.. i dont think they got a solution on how to use VNC when the server has no monitor

---

### Post by GavynRiebau on 2008-06-08
I have the exact same problem and would greatly appreciate a solution if anyone knows one.

---

### Post by Oysterville on 2008-06-09
Is it an X config issue?  I can hook a monitor up to the boxes if I have to, but I'd rather reduce the clutter.

---

### Post by AlanR8 on 2008-06-15
Similar here, but not quite the same.

When the "server" is connected to a monitor and keyboard all is well and viewing from the remote screen is fine. But detach the monitor and keyboard and the remote viewing window is very small. 

Looking at the remote settings the display has reverted to 600X480. Means I can't view settings menus etc. 

I also get the message "Connection failed. The server does not accept new connections" from time to time. The answer I've found is to hook up a monitor and mouse and kill the VNC session that seems to persist. After that I can log on "headless". This is the bit that pisses me off the most! 

Any answers gratefully accepted!

---

### Post by AlanR8 on 2008-06-18
Bump!!!!!

---

### Post by GavynRiebau on 2008-07-18
Ok I found a solution that worked alright for me so hopefully for you too:
(first make sure vnc4server is installed)

1. ssh/putty into monitorless server
2. enter "vnc4server :1"
3. enter "export DISPLAY=:1"
4. enter "x-session-manager &"
5. exit terminal session and you should now be able to vnc into the server with "vncviewer server_name :1"

---

### Post by Oysterville on 2008-07-21
Thanks for the update!  I'll give this a try when I'm at home tomorrow morning and report back.

It's really appreciated that you came back to post this, as this forum shows up a LOT in Google searches for Ubuntu topics so this will likely help others in the future.

---

### Post by bart777 on 2009-02-13
Great! Thanks a lot! I had a problem with dispaying vnc view of my monitorless server. Now it works perfect. I didn't even suppose it can looks so nice ;)

---

