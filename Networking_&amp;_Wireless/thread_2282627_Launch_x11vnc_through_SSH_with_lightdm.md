---
title: "Launch x11vnc through SSH with lightdm"
date: 2015-06-15
forum: Networking &amp; Wireless
---

### Post by spookybathtub on 2015-06-15
I'm running a Kodibuntu server, and I sometimes want to connect with VNC.
For security, I tunnel x11vnc through SSH, like this:
```
ssh -L 5900:localhost:5900 *hostname* 'x11vnc'
```

Then on my laptop, I connect to localhost with RealVNC Viewer.  This works fine in the Kodi UI, but I need to access the login screen to start a normal desktop environment to use a web browser, etc.  At the login screen, x11vnc fails to start because it can't find an X display.  So I add the following line to .x11vncrc:
```
auth /var/run/lightdm/root/:0
```

Now it works when I run x11vnc as root.  But I can't use sudo over SSH, and it seems like a bad idea for security too.  What can I do?

---

### Post by T.E.N. on 2015-06-17
> **spookybathtub said:**
> I'm running a Kodibuntu server, and I sometimes want to connect with VNC.
For security, I tunnel x11vnc through SSH, like this:
```
ssh -L 5900:localhost:5900 *hostname* 'x11vnc'
```

Then on my laptop, I connect to localhost with RealVNC Viewer.  This works fine in the Kodi UI, but **I need to access the login screen to start a normal desktop environment** to use a web browser, etc.  At the login screen, x11vnc fails to start because it can't find an X display.  So I add the following line to .x11vncrc:
```
auth /var/run/lightdm/root/:0
```

Now it works when I run x11vnc as root.Wondering **if x11vnc (or tightvncserver / vnc4server) still is the best approach in the first place** (though often recommended from the Gnome days, e.g. [https://answers.launchpad.net/ubuntu/+source/lightdm/+question/209394](https://answers.launchpad.net/ubuntu/+source/lightdm/+question/209394), [http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/](http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/)):

I'll sum up what is known as these are common and partly unresolved difficulties.

Current 14.04 LTS uses /usr/lib/vino/**vino-server by default** ([http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)) but starts it only once & while a user has logged on locally (usually into Unity. cf. [http://askubuntu.com/questions/4474/enable-remote-vnc-from-the-commandline](http://askubuntu.com/questions/4474/enable-remote-vnc-from-the-commandline)).

However, the /usr/sbin/**lightdm default** (also rather than earlier GDM) has no /etc/lightdm/lightdm.conf (just a /etc/lightdm/users.conf) and hence **no [VNCServer] section** either.

With the distinction between logon screen and actual desktop environment, the trouble remains as concisely described from another age & distro already at [http://www.mattnworb.com/post/10163223816/how-to-start-vnc-server-from-the-command-line](http://www.mattnworb.com/post/10163223816/how-to-start-vnc-server-from-the-command-line):[quote=Matt Brown]logging out of my physical session, thus terminating my VNC session and (GUI) access to the Linux desktop machine. To get back in, I **need to find someone in the office who can walk over to my Linux desktop and log me in again. This is obviously a bit annoying.**[/quote]Especially when there's no one around, or if you have to find out the hard way that even the best of them may have bad days when you shouldn't (en)trust them with any password...

From ssh -X -L 5900:localhost:5900 ... even while there is (only one) /tmp/.X0-lock, one can connect to the open local desktop of that user through the tunnel (e.g. vncviewer or vinagre) but not do any of the following (for that display or another):
[quote=export DISPLAY=:0.0 && /usr/lib/vino/vino-server]
No protocol specified

** (vino-server:8...6): WARNING **: Could not open X display
No protocol specified
Cannot open display: 
Run 'vino-server --help' to see a full list of available command line options[/quote]
[quote=startx]xauth: (stdin):2:  unknown command "b6................................................4"
xauth: (stdin):3:  unknown command "b6................................................4"
xauth: (stdin):4:  unknown command "b6................................................4"

X: user not authorized to run the X server, aborting.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error[/quote][quote=xhost]
No protocol specified
xhost:  unable to open display ":0.0"[/quote]

The "trusted", i.e. **not** secured, -Y variant lets you do a little more (but startx fails as above):
[quote=ssh -Y -L 5900:localhost:5900 ...]/usr/lib/vino/vino-server

** (vino-server:8...9): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-Ht..........cI: Connection refused

(vino-server:8...9): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion 'global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
17/06/2015 08:34:19 Autoprobing TCP port in (all) network interface
17/06/2015 08:34:19 Listening IPv6://[::]:5900
17/06/2015 08:34:19 Listening IPv4://0.0.0.0:5900
17/06/2015 08:34:19 Problems in NewSocketListenTCP()
17/06/2015 08:34:19 Listening IPv6://[::]:5901
17/06/2015 08:34:19 Listening IPv4://0.0.0.0:5901
17/06/2015 08:34:19 Autoprobing selected port 5901
17/06/2015 08:34:19 Advertising security type: 'TLS' (18)
17/06/2015 08:34:19 Re-binding socket to listen for VNC connections on TCP port 5901 in (all) interface
17/06/2015 08:34:19 Listening IPv6://[::]:5901
17/06/2015 08:34:19 Listening IPv4://0.0.0.0:5901
17/06/2015 08:34:19 Clearing securityTypes
17/06/2015 08:34:19 Advertising security type: 'TLS' (18)
17/06/2015 08:34:19 Clearing securityTypes
17/06/2015 08:34:19 Advertising security type: 'TLS' (18)
17/06/2015 08:34:19 Advertising authentication type: 'No Authentication' (1)
17/06/2015 08:34:19 Re-binding socket to listen for VNC connections on TCP port 5901 in (all) interface
17/06/2015 08:34:19 Listening IPv6://[::]:5901
17/06/2015 08:34:19 Listening IPv4://0.0.0.0:5901
17/06/2015 08:34:19 Clearing securityTypes
17/06/2015 08:34:19 Clearing authTypes
17/06/2015 08:34:19 Advertising security type: 'TLS' (18)
17/06/2015 08:34:19 Advertising authentication type: 'VNC Authentication' (2)
17/06/2015 08:34:19 Clearing securityTypes
17/06/2015 08:34:19 Clearing authTypes
17/06/2015 08:34:19 Advertising security type: 'TLS' (18)
17/06/2015 08:34:19 Advertising authentication type: 'VNC Authentication' (2)
17/06/2015 08:34:19 Advertising security type: 'VNC Authentication' (2)
17/06/2015 08:34:25 [IPv4] Got connection from client localhost
17/06/2015 08:34:25   other clients:[/quote]There just isn't an(other) X session to connect to by default (encodings below just to ensure usable compression over slow connections):[quote=vncviewer -encodings 'copyrect tight hextile' localhost:5901]Connected to RFB server, using protocol version 3.7[/quote]...followed by: nothing (unlike on port 5900 in this case).

If your machine is in such a secure place that you can configure auto-login to X on boot (and keep it running all the time), you're in luck:
You could just configure vino-preferences to make the standard VNC serve that one by default (see [http://ubuntuforums.org/showthread.php?t=1017746&p=6412467#post6412467](http://ubuntuforums.org/showthread.php?t=1017746&p=6412467#post6412467) though).

Otherwise (i.e. usually), there are two solutions we should refine and document in general, using Ubuntu defaults as much as possible:
[LIST]
[*]Start X (then running vino-server by itself once the desktop environment is up) from a Secure SHell **without graphical LightDM logon**.
[*]Use LightDM through vino-server (through SSH tunnel):
Trouble is, how could this allow us to both access the current active desktop (if any) **and** create a new one (for another user) **and** access that all within the same VNC session?
[/LIST]

---

### Post by spookybathtub on 2015-06-17
Thanks for the detailed reply.  I must admit this is a bit over my head.  

I did try vino at first (months ago), and I switched to x11vnc because it just seemed to work better, but I can't remember exactly why.

This machine is a home media center, so it's set to auto-login to the Kodi session and stay running all the time (not sure if that's considered X).  Are you saying I could keep Kodi running on the connected display, and use vino to serve an alternate desktop session on demand to VNC clients?  That would be awesome.

---

### Post by T.E.N. on 2015-06-17
> **spookybathtub said:**
> I did try vino at first (months ago), and I switched to x11vnc because it just seemed to work better, but I can't remember exactly why.

This machine is a home media center, so it's set to auto-login to the Kodi session and stay running all the time (not sure if that's considered X). Are you saying I could keep Kodi running on the connected display,It's a GUI for the local screen, so presumably yes on both if [http://forum.kodi.tv/showthread.php?tid=74791](http://forum.kodi.tv/showthread.php?tid=74791) is any indication...
> and use vino to serve an alternate desktop session on demand to VNC clients?  That would be awesome.That's the idea how it should be feasible.
Both vino-server and x11vnc are supposed to give access to a running Desktop Environment (DE), but should also be able to export a GUI session independent of the physical screen (have been assisting xrdp users this way for some years, who were using e.g. Firefox via Thin Clients on top of much more lightweight DEs than Unity), to which some other VNC servers are limited.

What this thread should really figure out and document for current Ubuntus is how to make all of this possible, i.e. login & start an X session through lightdm or otherwise for a specific user, and access it over VNC (whether on the currrent desktop or just in memory) while keeping settings as secure as possible.
What processes need to be started for the second instance of vino-server to have something to export via VNC depends on the DE, and particularly little information can be found in this respect for the current default combination of LightDM then Unity.

---

### Post by T.E.N. on 2015-06-17
[http://ubuntuforums.org/showthread.php?t=1489602](http://ubuntuforums.org/showthread.php?t=1489602) joined by x11vnc's author has some hints on setting up what you had in mind.

---

