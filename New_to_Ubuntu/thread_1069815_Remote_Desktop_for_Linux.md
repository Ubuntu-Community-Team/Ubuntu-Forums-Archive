---
title: "Remote Desktop for Linux?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by psychx on 2009-02-14
I have the newest Ubuntu.

I was wondering if I can set up a remote-admin/remote-desktop to access my computer from work. I use Windows XP at work.

Mainly just to keep setting up things while not busy at work.

---

### Post by damis648 on 2009-02-14
Just head over to System>Preferences>Remote Desktop and enable it and play with the settings :-). To be able to access it from work, you have to forward the port you will be using for VNC on your computer through your router. The default port it 5900, so what you have to do is go into your router configuration and forward port 5900 to your local IP. At work, just install a VNC Viewer (like [this]("http://www.realvnc.com/cgi-bin/download.cgi") one) and you can just pop in your IP at your house (find with whatsmyip.com).

---

### Post by psychx on 2009-02-14
Thanks a lot, I wasn't sure if it was built in or if I had to get it. I will be playing around with this, hopefully I have it set-up right :)

---

### Post by cerealtx on 2009-02-14
> **damis648 said:**
> Just head over to System>Preferences>Remote Desktop and enable it and play with the settings :-). To be able to access it from work, you have to forward the port you will be using for VNC on your computer through your router. The default port it 5900, so what you have to do is go into your router configuration and forward port 5900 to your local IP. At work, just install a VNC Viewer (like [this]("http://www.realvnc.com/cgi-bin/download.cgi") one) and you can just pop in your IP at your house (find with whatsmyip.com).

yah, i setup a irc bot that when i send it a command it sends me its WAN ip address so i can connect to it :P

---

