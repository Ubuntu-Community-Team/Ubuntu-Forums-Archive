---
title: "VNC Viewer will not accept keyboard input!!"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by rubrboots on 2008-01-17
I am using 7.10 Gutsy, and am not able to vnc to a knoppmyth maching on the network. When I start vncviewer or any other vnc program the type server address dialog box pops up but the text box will not accept keyboard input. I know the server works properly since I can vnc to it from my windows computer but not with Gutsy. Any ideas?

---

### Post by tobydeemer on 2008-02-19
I have this issue as well. Any ideas at all would be greatly appreciated. I've gone through several tutorials and the help.ubuntu docs, and I have everything configured properly, (though obviously not 100%). I know the machine (Windows Server) can be remoted to, as I did it using RDP. However, we implemented a VNC connection to be more secure and we have DynDNS as well, so I need to use VNC.

When I start VNC Viewer on my machine, I get to the Win desktop, and can move the login window around on the viewed desktop, but it will not respond to keyboard input. Right clicking anywhere does nothing either.

Help?

Thanks.

---

### Post by tobydeemer on 2008-02-19
Umm... I just figured this out. It was really simple actually and I feel silly. I looked in the RealVNC FAQs on their homepage (duh) and there was one "I can see the remote desktop but Ctrl+Alt+Delete is intercepted by my own computer" and their fix was to hit F8 which opens the VNC Viewer drop down menu (WOW!) and click "Send Ctrl+Alt+Delete".

That worked wonders.

---

### Post by Mazrick on 2008-03-23
Bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/147648](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/147648)

It's fixed in Hardy, but there is a workaround for gutsy that worked for me!
Just change focus to something else, then back to the password box, then your cursor appears in the box and you can enter text.

> **rubrboots said:**
> I am using 7.10 Gutsy, and am not able to vnc to a knoppmyth maching on the network. When I start vncviewer or any other vnc program the type server address dialog box pops up but the text box will not accept keyboard input. I know the server works properly since I can vnc to it from my windows computer but not with Gutsy. Any ideas?

---

