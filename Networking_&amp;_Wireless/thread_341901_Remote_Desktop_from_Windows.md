---
title: "Remote Desktop from Windows"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2007-01-19
I have my ubuntu server ready to go.  It will be our locations first Linux server.  It will be installed right on top of 10 Windows servers in our server room.  I think it should be on top.

Once I set-up the Remote Desktop under System->Prefrences-Remote Desktop how do I access it from a WinXP box.  Same way I remote to a windows box or is their some special software I need to use on the windows box?

---

### Post by Nik_Doof on 2007-01-19
It'll be using VNC, [UltraVNC]("http://ultravnc.sourceforge.net/") is a good Windows client.

---

### Post by SendDerek on 2007-01-19
RealVNC is the only way I can think of right now... Fairly simple setup really.  Download the program, install it, and run VNC Listener from the Start menu.  Type in the IP addy or the Server's name and you'll connect.  Be sure to have "Allow others to control my desktop" checked in the remote desktop options.

I'm going to subscribe to this thread because I'm interested in other ways of doing it also.

---

### Post by weaver4 on 2007-01-19
Thanks guys!!!!


How do I change Remote Desktop on the ubuntu server to use another port rather than 5900?

---

