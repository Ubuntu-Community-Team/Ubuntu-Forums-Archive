---
title: "All VNC, Remote Desktop viewer display problem"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by hman1169 on 2011-01-08
It seems no matter what protocol I use to connect, I am only getting a "Snapshot" of the server's desktop. I cannot see Icons or movement. Each of the computers I am trying to connect to are running the "Remote Desktop" and it is configured to accept connections and users must enter a password, but when I log in, I see their desktop wall paper and cannot do anything. Because this is happening on two separate computers I believe the problem is in my settings somewhere... Both of these computers were put together by me with a promise that I can come in and help them when they need it... (Even though I am not the master) I have found the solution to just about ever problem I have encountered here on the web, except for this one. I just can't seem to find a solution.

It is like I only get a screen shot of their wallpaper and can not do anything. Sometimes I can see my mouse and or a pointer, but that's it. 

Have I missed a setting?

Thanks in advance!
Chris

---

### Post by joddy on 2011-01-12
This is a common issue I have encountered when using Nvidia or other proprietary graphics drivers.

Two possible solutions:

a) Disable compiz: System->Preferences->Appearance
   On "Visual Effects" tab, select "None"

   Now try if things work better.

b) Forget about Ubuntu's Remote Desktop, disable it and use x11vnc instead.

First, you need to install it:
[PHP]sudo apt-get install x11vnc[/PHP]

and then run x11vnc, for example (many other options available), and leave it running

[PHP]x11vnc -forever -noxdamage -passwd "mypassword" & [/PHP]


then attempt to connect from the remote PC. Good luck.

---

### Post by hman1169 on 2011-01-22
I am sorry for sounding so stupid, but is this direction for the "Host" is that where the problem is?

---

