---
title: "How to connect to windows 2003 server using remote desktop /console option"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by B3rt on 2007-05-20
I am currently switching from Windows XP to Unbuntu 7.04 (still running XP as dual boot).

I have to connect for my work regularly to several Windows 2003 servers using remote desktop. (terminal)
On the servers are processes running which have a console opened, to see this information on the desktop of the server in XP you have to add /console to the startup of the remote desktop client.

When you do this you log into the server as if you where actually behind the keyboard, you can see the full desktop of the server with all its programs, when you leave /console away you just login as a user and do not see the actual desktop.

This is what the remote desktop clients do in Ubuntu, I can connect but I do not see the processes (consoles) of the applications which are running, this results that I cannot work using the Ubuntu on the Windows servers.
I still have to boot into XP and use the default remote desktop client of XP to work.

Does someone know this problem and knows a solution for it?
Changes on the server itself are NO option, so no VNC or other remote software can be installed or used on the servers!

---

### Post by veloce on 2007-05-21
Is this any help?

[http://headblender.com/joe/blog/old/001166.html](http://headblender.com/joe/blog/old/001166.html)

With Terminal Services Client you can save an rdp file - I assume you could then edit it.

---

### Post by wtfbrb on 2007-07-30
I added the line connect to console:i:1 and it didn't work for me.  This is the only xp computer I have not switched to ubuntu because I can't connect to the console session of my 2003 server.

Anyone else had any luck?

---

