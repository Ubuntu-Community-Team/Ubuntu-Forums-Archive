---
title: "xdmcp through the internet."
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by kameleon25 on 2007-05-02
I am trying to get a RDP type setup for my linux box. I am running 7.04 ubuntu as we speak. I am trying to move away from winblows so any help is appreciated. Here is my situation: I have been having to use VNC to connect to my machine here at home from my pc at work. I do various things on this machine mainly I run GAIM and keep Firefox open in case I need to test a website from outside our network. But here is the issue. I need it to when I am logged on to my machine here at home remotely that it locks the desktop locally. Just like RDP does in winblows. I don't want it to where there is a separate X session for the remote connection if at all possible.  I like the way that NX sounds except the way I read it is you cannot resume the X session locally. Is there any way to do this? 

Thanks in advance.

---

### Post by scxtt on 2007-05-02
you can share your :0 "connection" or session ... just install x11vnc ... i'm not real sure what it does "locally" when you use it remotely - i imagine someone could watch you doing stuff and maybe even annoy you by using the mouse, but that's the price you pay :p ...

---

### Post by kameleon25 on 2007-05-02
Thanks for the uber quick reply. But that is the kind of thing I want to avoid. Around my house I never know who is around. I don't want someone to come to my pc, sit down, and just watch what I am typing. I do have quite a bit of security related things that I do and sometimes I will relate things via IM which is of course running on this pc. With all the wealth of knowledge out there, it has to be a way to do what I need. ;)

---

### Post by scxtt on 2007-05-02
why are you so opposed to a separate session? (you can always use vncviewer to connect back up to any vncserver session you've started previously) ... i've seen something about a linux RDC-like protocol - never tried it myself ...

---

### Post by kameleon25 on 2007-05-03
The only reason I am opposed to a seperate session is ONLY if I cannot connect to it locally. See what I mean? ONce I get home I would like to be able to log into the local machine and have all my stuff there just as I left it when I left work. Just like M$ Remote Desktop Protocol does. I know that the "server" edition of ubuntu is supposed to have the LTSP-5 stuff in it but I doubt it is to where one could log in locally if they wanted to and gain the same desktop. If there was a way to connect to the "remote" desktop locally and it be just like I am sitting on the machine (which I would be) that would be awesome. The main thing is while at work I need the local display locked and output only viewable to me remotley. Then once I get home and all the security stuff is done I can log back into the same desktop and check my mail, chat on GAIM (err pidgin lol), work on some images in GIMP, and listen to music etc. All on the same "desktop" if possible. If not then I guess I will be doing the NX deal since it handles low bandwidth issues well and then just log out of it and log back in locally once I get home. I am one that I just like to have programs open and leave them running (like GAIM and Firefox) so I don't lose the info. FF session restore don't always bring all the pages back up. :)

---

### Post by scxtt on 2007-05-03
you can start a vnc server, which would be your :1 connection - start up any and all programs you want to use and use them throughout the day ... then just close the viewer you're using to view your :1 connection remotely when you're done w/ it - everything will still be there waiting for you ... then when you get home do something like: **vncviewer localhost:1** and you can resume it from your :0 session ... there really isn't any way to mix :0 and :1 (like what you're thinking of w/ RDC, and it locking :0 when you connect remotely) but really there's not much difference ...

---

### Post by krunge on 2007-05-03
You can run a virtual VNC session (and NX too I believe) that gives remote access, and when you are local you just start up a naked X server (no window manager or desktop) that ONLY runs the viewer directed at the server that is local.

The traditional way to do the local access for VNC is to have, say, a $HOME/.xinitrc that looks something like:
```

#!/bin/sh
vncviewer -geometry +0+0 -encodings raw -passwd $HOME/.vnc/passwd localhost:5

```
(the newer viewers, e.g. realvnc's, will have different names for the command line options). It might not be .xinitrc, maybe .xsession, or .Xclients, or whatever. You will have to figure out how your distro+X does this.   The above assumes the vnc server is running on :5 (i.e. port 5905).

This was the original design plan for VNC on Unix.  It is a nice model, but I don't think many people do it.     Perhaps because it is slower locally than using full capabilities of the native X server, i.e. not much or no H/W video acceleration, but video cards are so fast these days even no acceleration is fast enough for most work. Or perhaps people don't do it just because it feels odd.

I know one person who uses x11vnc with the Xdummy hack ([http://www.karlrunge.com/x11vnc/#faq-xvfb]("http://www.karlrunge.com/x11vnc/#faq-xvfb")) to do this and claims it gives good local response, even for watching DVD's.

I do not think there is support in the X server to not send graphics to the hardware framebuffer to do the windows RDP-like thing you want.  I guess it is possible but I don't see an API to do it (if you find one let me know).  With x11vnc people with your concern mainly just hope the screen blank stays on while they remotely access the display. There is a kludge to improve this a bit: [http://www.karlrunge.com/x11vnc/#faq-blockdpy]("http://www.karlrunge.com/x11vnc/#faq-blockdpy"),  (e.g. the -forcedpms option) but neither is very secure.  And of course if someone has physical access to the machine they pretty much can do anything they want to if they are devious enough.

---

### Post by dbott67 on 2007-05-03
As mentioned by Karl in his post, there is a package called NX ([www.nomachine.com]("http://www.nomachine.com")) that allows you to create a secure remote desktop over SSH.

If you create a secondary "NX" account, you would be able to login remotely and do your work.  When you're done you could "suspend" the session and then re-connect when you get home (you'd need to use the NX client to resume your session under the "NX" user account).

See attached screenshot.

-Dave

---

### Post by krunge on 2007-05-04
```
#!/bin/sh
vncviewer -geometry +0+0 -encodings raw -passwd $HOME/.vnc/passwd localhost:5

```

I forgot to mention, if you can't find the name and location of the X startup file that your system uses (i.e. it is not $HOME/.xinitrc), just put the above command in a shell script in your PATH.  Suppose you named it "vnclocal" (or "nxlocal" with the analogous nx command).

Then when sitting at the local machine log in normally however choose Failsafe as your Session type.  Once the  session starts up, just type "vnclocal" in the terminal to connect to your local vnc server.

This might give a little bit more flexibility because you can easily choose a new local X session by not selecting Failsafe.

---

