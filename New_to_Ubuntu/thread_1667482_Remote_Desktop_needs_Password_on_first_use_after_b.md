---
title: "Remote Desktop needs Password on first use after boot"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by jimwims on 2011-01-14
I am attempting to access and controlling my Ubuntu 10.10 desktop running Remote Desktop over the Internet from my iPad using VNC Viewer.  In my application, I am able to start the desktop remotely, and I want to be able to then access and control the desktop with it completely unattended.  My setup works fine except for one thing.  On the first attempt to access the desktop after it has booted up, a box comes up on the desktop screen requiring the entry of a password at the desktop.  This defeats my entire purpose.  Any suggestions on how I can avoid this?  Thanks.

Jim

---

### Post by bodhi.zazen on 2011-01-14
First you should understand the security implications of what you are doing. VNC is by far the most commonly cracked server and I would now use it in this way.

First, do you need a graphical interface ? If not use ssh or ssh -X.

Second, if you must, convert to FreeNX.

Third, if you still want to use vnc, use an alternate VNC server. The default (vino) requires you are logged in locally. try vnc4server.

---

### Post by jimwims on 2011-01-15
Thank you very much for your reply.  I do need a GUI because I don't know enough about Ubuntu to get along without one.  FreeNX does not appear to have an iPad version, so I don't think that will work.  So I will try vnc4server.

---

### Post by Lenny212 on 2011-01-17
I have typed in "vnc4Viewer" in Terminal. On prompt I entered password. I think this means my VNC Server is now running is that right? Do I need to do anything else?

I downloaded Mocha VNC Lite onto my iPhone. I entered my IP Address (found at [http://www.whatismyip.com/](http://www.whatismyip.com/)), port 5901 and password.

I immediately get message cannot connect to host [ipaddress], port 5901.

Do you have any ideas what more I need to do?

---

### Post by Lenny212 on 2011-01-17
I have typed in "vnc4Viewer" in Terminal. On prompt I entered password. I think this means my VNC Server is now running is that right? Do I need to do anything else?

I downloaded Mocha VNC Lite onto my iPhone. I entered my IP Address (found at [http://www.whatismyip.com/](http://www.whatismyip.com/)), port 5901 and password.

I immediately get message cannot connect to host [ipaddress], port 5901.

Do you have any ideas what more I need to do?

---

### Post by Lenny212 on 2011-01-17
I have typed in "vnc4Viewer" in Terminal. On prompt I entered password. I think this means my VNC Server is now running is that right? Do I need to do anything else?

I downloaded Mocha VNC Lite onto my iPhone. I entered my IP Address (found at [http://www.whatismyip.com/](http://www.whatismyip.com/)), port 5901 and password.

I immediately get message cannot connect to host [ipaddress], port 5901.

Do you have any ideas what more I need to do?

---

### Post by ikt on 2011-01-17
> **Lenny212 said:**
> I have typed in "vnc4Viewer" in Terminal. On prompt I entered password. I think this means my VNC Server is now running is that right? Do I need to do anything else?


vnc4**server** vs vnc4**viewer**

vnc comes in 2 parts, a server and a viewer, a viewer is used to connect to the server, you need to be installing the server on the computer you want to connect to.

---

### Post by diablo75 on 2011-01-17
To setup your VNC Server (on the Ubuntu machine) you will need to go into your System>Preferences>Remote Desktop menu and enable it, as well as customize any security settings you want to have (such as requiring a password or physical user authorization).  By default your system will be listening for an incoming connection request on port 5900, the default port for VNC.

On your client/viewer side, you just have to tell it to connect to the IP address of the computer you setup.

You had mentioned a box appearing asking you for a password.  This box is either:

1.  VNC viewer being asked by VNC server to provide password
2.  Your screensaver came on and locked your account out in the process, which would make sense if you were able to connect via VNC without typing in a password but were then told to type one in anyway.  If that's the case, disable your screensaver or at least disable the password prompt/lock feature within your screensaver settings.

---

### Post by ikt on 2011-01-17
> **diablo75 said:**
> To setup your VNC Server (on the Ubuntu machine) you will need to go into your System>Preferences>Remote Desktop menu and enable it

> **bodhi.zazen said:**
> Third, if you still want to use vnc, use an alternate VNC server.** The default (vino) requires you are logged in locally. try vnc4server**.

How to Install a VNC Server in Ubuntu

[http://www.ehow.com/how_5089245_install-vnc-server-ubuntu.html](http://www.ehow.com/how_5089245_install-vnc-server-ubuntu.html)

Seems a lot more complicated but at least it doesn't have the security concerns related to the default install.

---

### Post by jimwims on 2011-01-17
Thanks very much for this.  These instructions worked well for me and vnc4server seems to be meeting my needs.  In addition to the instructions, I did have to add vnc4server to the startup programs.  I also deleted Remote Desktop from the startup programs. 

One question: when using vnc4server, my VNC client does not display the same screen as is shown on the desktop monitor.  Specifically, as the disply on the VNC client changes because of mouse and keystroke actions taken at the client, the desktop monitor does not show these same changes.  Is there a way to get the displays to be the same?

---

### Post by bodhi.zazen on 2011-01-17
> **jimwims said:**
> Thanks very much for this.  These instructions worked well for me and vnc4server seems to be meeting my needs.  In addition to the instructions, I did have to add vnc4server to the startup programs.  I also deleted Remote Desktop from the startup programs. 

One question: when using vnc4server, my VNC client does not display the same screen as is shown on the desktop monitor.  Specifically, as the disply on the VNC client changes because of mouse and keystroke actions taken at the client, the desktop monitor does not show these same changes.  Is there a way to get the displays to be the same?

Yes, go back to the default VNC server.

Basically you have two options

1. Use a VNC server that uses a shared X session. In this case you will need to be physically logged in on the server (this was the original problem on your original post).

2. Use a vnc server that uses a separate X session. This is what you get with vnc4server.

I do not know a vnc server that will do both.

---

### Post by jimwims on 2011-01-17
OK.  Thanks very much for your help.

---

