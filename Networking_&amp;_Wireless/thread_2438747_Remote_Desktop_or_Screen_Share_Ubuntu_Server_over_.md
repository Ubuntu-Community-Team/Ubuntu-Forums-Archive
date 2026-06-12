---
title: "Remote Desktop or Screen Share Ubuntu Server over SSH?"
date: 2020-03-17
forum: Networking &amp; Wireless
---

### Post by shapiror06 on 2020-03-17
Hey all. I've used Ubuntu desktop many times in the past, but never in a server environment.

What I want to do seems like it would be simple, I just don't have any experience with it.

I installed Ubuntu Server on an system that is connected to my local network via wifi, and has just a power source connected to it. I am able to connect to it via SSH with Putty on my Windows machine also on the same network.

What I would like to do is see what is happening on the active session on the server. I guess this would be called remote desktop or screen sharing, even though there is no desktop environment running on the server.

Currently when I connect to the server through Putty, it's like opening a new terminal session and I cannot see what is actively running on the server itself.

Is what I want to do possible, and if so, can someone give me some guidance?

Thanks! -Randy

---

### Post by Tadaen_Sylvermane on 2020-03-17
Research a vnc server. You will need to install a desktop environment to use it. That being said I think you would be better served learning how to use the terminal a bit more rather than relying on the gui. Over wifi gui will move like molasses. Wifi is good. Will never be as good as a gigabit wire though. Even 10/100 would be better than wifi.

---

### Post by HermanAB on 2020-03-17
The utility called 'top' will show you what is running.

If you want to remote execute a GUI program on the server, then you first of all have to have the GUI program installed on the server, which usually with a true server installation would not be the case.  So you need to install a desktop environment on the server, even though you need not actually run the DE.  You need not run X on the server, since you can run individual remote X programs over ssh, using your local X server:
$ ssh -X user@server 'dolphin [http://www.cnn.com](http://www.cnn.com)'

A remote browser will then pop up on your local desktop, if your local desktop is running X (and not Wayland).

---

### Post by Tadaen_Sylvermane on 2020-03-17
Herman's idea better than mine. Individual apps instead of a whole gui. Still don't expect much over wifi.

---

### Post by slickymaster on 2020-03-17
Thread moved to **Networking & Wireless** for a better fit

---

### Post by TheFu on 2020-03-17
Using Windows as the client is probably the largest problem.  A Linux workstation with a GUI would make all of this stuff pretty easy.  It is because X11 is almost always available on any Linux workstation. Same for ssh. Together, those are an amazing combination.

But ....
a) Unix servers don't have any GUI.  Running a GUI makes for a bloated server and should be avoided.  ssh is the normal way to manage **EVERY** Unix/Linux server in the world. We don't load GUIs or GUI programs onto servers.

b) You **can** load a minimal X/client onto a Linux server, if you must. You don't need or want a full bloated DE.  I usually just load an 'xterm' program to get the minimal dependencies pulled in, then just the 1 or 2 other GUI programs (X/Clients) that I need.  The "client" runs on the remote system. The X/Server runs on the workstation you sit behind and displays the client window, passes the mouse and keyboard events to the client, etc.  This is exactly the opposite from almost every other Client/Server setup.  X11 has to be used, not Wayland.

c) VNC is a terrible solution. It is slow and highly non-secure. There are better choices, but those really shouldn't be used to connect to any Unix/Linux server.  Stay with ssh and learn to use the shell and CLI interfaces for everything.

I've been a Unix admin about 25 yrs now. Here's what I do on all my new servers, when they are first brought onto the network: [https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

Some other ideas around displaying GUI programs remotely:  [https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)  I need to update that article for new stuff (basically, use x2go).  But for fast network connections,  **ssh -X userid@remote_machine remote-command options** really is the best, easiest answer for Unix-to-Unix GUI stuff.  

Windows doesn't have any X/Server to my knowledge without paying $130 for a commercial solution.  Getting those commercial answers working is non-trivial for people unfamiliar with X/Windows.  Many people will run a lite Linux virtual machine just for the X/Server stuff.  Even the smallest distro - like a 64MB TinyCore has a fully capable X/Server.  There is Xming for Windows, but it was a really terrible implementation last time I looked at it. Between the 3 choices - pay, xming or use a VM, using a VM is the one I'd choose.

---

