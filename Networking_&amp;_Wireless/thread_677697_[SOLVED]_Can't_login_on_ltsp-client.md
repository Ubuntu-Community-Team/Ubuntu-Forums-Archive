---
title: "[SOLVED] Can't login on ltsp-client"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by angelot on 2008-01-25
I've just installed ltsp standalone on my ubuntu server 7.10.

Everything went fine.

I boot the client and I get the login-screen.

Then I try to login as one of my users on the server and I get this errormessage:
```
Xsession: Unable to start xsession --- no &quot;/home/myusername/.xsession&quot; file, no &quot;home/myusername/.Xsession&quot; file, no session managers, no windowmanagers, and no terminal emulators found; aborting.
```
I have have no GUI (no xserver) on my server - didn't know that I had to have one to get LTSP up?

I Ctrl-Alt-F1 and try login from a shell. This time I get "login incorrect" using the same username/password.

I don't have any users in /opt/ltsp/i386/home/ on server and no .xsession file in /home/myusername on server.....

I also tried "cp /etc/X11/Xsession ~/.Xsession" on server, and now I don't get the errormsg anylonger on the client - just a black screen doing nothing. I'm still getting "login incorrect" when trying to login in a shell on the client....

After some searching I also tried (from server):
sudo ltsp-update-kernels
sudo ltsp-update-sshkeys
sudo ltsp-update-image
No errors - everything went fine, but still no login on the client....

How can I fix this?

Angelot

---

### Post by maybeway36 on 2008-01-25
I think you do need some X app on the server. Try installing xterm; it's small and should work.

---

### Post by angelot on 2008-01-25
OK - I installed xbitmaps and xterm, but how can I make a .xsession-file in my homedir on the server?
```
~$ xterm
xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set
~$
```

---

### Post by angelot on 2008-01-27
I've just installed edubuntu-server 7.10 and finally ltsp is up and running with no problems :lolflag:

And - yes, edubuntu installs by default GNOME and all the Edubuntu colors...

I belive to get ltsp running you'll have to have a working X-enviroment on the server....

Thanks for all help...

---

