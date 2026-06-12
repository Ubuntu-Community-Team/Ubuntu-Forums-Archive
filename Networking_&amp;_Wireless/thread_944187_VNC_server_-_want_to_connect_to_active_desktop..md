---
title: "VNC server - want to connect to active desktop."
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by dchurch24 on 2008-10-11
Hi all,

I have an old machine that I have put in my kids bedroom - the eldest is 6, and while she is quite good at using both Windows and Xubuntu (I chose that as the hardware was oldish), she gets stuck sometimes using GIMP etc...

I live in a flat with 3 floors and I'm on the bottom, and to be honest it's a pain in the a**e having to run up three flights of stairs just to find out she's on the wrong layer or something similar.

I have installed a VNC server on the machine, but every time I run it I get a new desktop.

How do I get the vncviewer to open and show her active desktop?

---

### Post by superprash2003 on 2008-10-11
> I have installed a VNC server on the machine, but every time I run it I get a new desktop.

get a new desktop?? didnt get you?

---

### Post by ee19921 on 2008-10-11
I think dchurch24 wants to see the session daughter is using to help remotely and doesn't want to create a new session everytime.

---

### Post by dchurch24 on 2008-10-12
That's exactly it - you put it much better than I did!

---

### Post by DannyB2 on 2008-10-12
It is possible to VNC to any active X11 gui session that is working.  I do it all the time.  You need to not be afraid of the command line.  Here is how I do it.  I SSH into my box, forwarding port 5900 (the VNC port).  While logged in, I run this command:

x11vnc -display :0 -auth .Xauthority

(You must install the x11vnc command, via. apt-get or your favorite package mangler.)

A bunch of text will appear, but in a nutshell, a VNC server is now running that is connected to whatever X session is on display :0 (the primary GUI).

Then I use my VNC client to connect to localhost:5900, since 5900 is forwarded over the SSH connection I'm using.  Poof!  I can now see, or operate my desktop on my other machine.  (BTW, I do this from work where I must use Windows, and therefore Putty and TightVnc.)

If the machine is on your private LAN and you're not worried about security, you could put the above x11vnc command into a startup script of the person you want to monitor.  Then, anytime, you can just VNC to the box on its 5900 port.

If several users are VNC'ed in, each with their own separate desktops, they all have display numbers, such as :1, :2, :3, etc.  You can also X11vnc to those.

Suppose your login user is "joe", and the person who is using the computer is "jane".  In order to get to jane's .Xauthority file, you must become jane.  Therefore to this...

ssh [email]joe@somewhere.com[/email] -L 5900:localhost:5900
sudo bash
su jane
cd ~jane
x11vnc -display :0 -auth .Xauthority

Then use VNC client to connect.  Hope that helps.

---

### Post by dchurch24 on 2008-10-12
Hi, thanks for the reply - that's exactly what I'm after.

However, I tried the above, and got this:

```

12/10/2008 16:37:20 x11vnc version: 0.9.3 lastmod: 2007-09-30
12/10/2008 16:37:20 
12/10/2008 16:37:20 *** XOpenDisplay failed. No -display or DISPLAY.
12/10/2008 16:37:20 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
12/10/2008 16:37:20 *** 1 2 3 4 

```

I then tried:

display=192.168.1.2:0
export display

and then tried again, but got the same.

---

### Post by ee19921 on 2008-10-13
> **dchurch24 said:**
> Hi, thanks for the reply - that's exactly what I'm after.

However, I tried the above, and got this:

```

12/10/2008 16:37:20 x11vnc version: 0.9.3 lastmod: 2007-09-30
12/10/2008 16:37:20 
12/10/2008 16:37:20 *** XOpenDisplay failed. No -display or DISPLAY.
12/10/2008 16:37:20 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
12/10/2008 16:37:20 *** 1 2 3 4 

```

I then tried:

display=192.168.1.2:0
export display

and then tried again, but got the same.


I am not expert. Can you try running the x11vnc command in home directory or add ~ prefix as in ```
x11vnc -display :0 -auth ~/.Xauthority
```

---

### Post by martin_legion on 2008-10-17
I have a slightly different problem:
When I connect to the vncserver I get an empty X session with a xterm and nothing else.
I run vncserver (tightvncserver) as a user in the server machine.
I want to connect to a new gnome session through vnc. I don't want to share the gnome desktop, I want to be able to log remotely through vnc so I can administrate the computer without interfering with the user in that PC.
Any ideas?

---

### Post by ee19921 on 2008-10-17
> **martin_legion said:**
> I have a slightly different problem:
When I connect to the vncserver I get an empty X session with a xterm and nothing else.
I run vncserver (tightvncserver) as a user in the server machine.
I want to connect to a new gnome session through vnc. I don't want to share the gnome desktop, I want to be able to log remotely through vnc so I can administrate the computer without interfering with the user in that PC.
Any ideas?

I am sure it is something about the ~/.vnc/xstartup file, adding a command to start gnome session should work. Can you post the contents of it?

---

### Post by martin_legion on 2008-10-17
Here's is my xstartup
I think I once tried uncommenting those two lines but I think it didn't change anything...

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &

```

---

### Post by ee19921 on 2008-10-17
> **martin_legion said:**
> Here's is my xstartup
I think I once tried uncommenting those two lines but I think it didn't change anything...

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &

```

Instead of "twm&", for kde use "startkde&" and for gnome "gnome-session&"(i think!).

---

### Post by dchurch24 on 2008-10-22
> **ee19921 said:**
> I am not expert. Can you try running the x11vnc command in home directory or add ~ prefix as in ```
x11vnc -display :0 -auth ~/.Xauthority
```

Thank you, it worked that time.

Inadvertently, you have contributed to my enlarging midrift! ;-)

Seriously though, thanks for the time - it always amazes me how helpful people are.

---

### Post by ee19921 on 2008-10-22
> **dchurch24 said:**
> Thank you, it worked that time.

Inadvertently, you have contributed to my enlarging midrift! ;-)

Seriously though, thanks for the time - it always amazes me how helpful people are.

I am happy to help with the midrift thing! :D

---

