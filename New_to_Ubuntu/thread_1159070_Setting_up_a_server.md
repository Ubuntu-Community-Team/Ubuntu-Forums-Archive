---
title: "Setting up a server"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-05-14
Hi all, (I know it might come as a shock, but I have another question!!)

I've just gotten a new PC which has become my main desktop, so I wanted to turn my older
pc into a server. (Server = P4, 1GB of ram, about 100GB of space for storage, as I dual
boot with windows).

The main uses for the server is to be used as a downloading machine (Linux .iso's and
such). I want to keep it downstairs so that I can plug it directly into the router, and
so that I can leave it on all night without the noise doing my head in.

I want to be able to control the server from either my desktop or my friends desktop,
both of which are located upstairs. And connected to the router via wireless.
(I'd prefer use a GUI for the remote desktop administration, rather than the cli).

My main questions are =

1. What software do I need to install on both desktop(s) and server to accomplish this?

2. What extra precautions do I need to take, considering that the server will probably be
   left on 24/7.

3. Do I need a static IP address for the server? How do I assign one?

4. Is there anything else that I need to take into consideration?


Thanks in advance for any help.

---

### Post by MegaJim on 2009-05-14
Remote Access via GUI is possible with ubuntu, just enable it from the preferences menu.

You'll need the free VNC Viewer for your windows pcs or Remote Desktop Viewer for the linux boxes.

You can setup a static IP address by right clicking network manager and choosing edit connections, edit the appropriate connection and set it to a static IP (IPV4 settings -> Manual, then add an IP), which IP you use will depend on the router setup, but generally anything in the range 192.168.1.2-99 will be fine, and the Gateway/DNS will be the IP of your router (usually 192.168.1.1) with a netmask of 255.255.255.0

If you're concerned about security, you can install GFW and restrict access to port 5900 (remote desktop port) to only your IP address or the local network.

You can then admin the machine remotely.

Next if you want to actually be able to transfer data you'll have to setup some sharing folders, there are plenty of ways to do this but the simplest is just to right click a folder and click Sharing Options then enable sharing

You can setup a "drop" folder with write access too if you want to dump something on there.

This isn't the only way to do it, but its probably the easiest, and its what I use at home so know it works.

---

### Post by GeordieJedi on 2009-05-14
Cheers MegaJim, Thats really usefull.
I apreciate the help mate! :-D

---

