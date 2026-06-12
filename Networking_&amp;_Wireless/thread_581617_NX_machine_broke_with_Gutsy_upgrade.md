---
title: "NX machine broke with Gutsy upgrade"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by rdoolen on 2007-10-19
I had a great NX server set-up that broke when I upgrades to Gutsy. 

I had FreeNX server running on my home office desktop. I could log in from my office at work with NX client for window XP. I could also login from my laptop running NX client on XP (recently change to Ubuntu 7.10 but that didn't seem to cause any issues). I could even suspend a session started from my office desktop and continue it on my laptop. When I got home, my home desktop work fine too, I could even continue a session if I used NX Client from a different account on the same machine.

All the versions of NX are 3.0. 

Then I upgraded my home desktop to Gutsy. Now I am having serious issues with screen resolution. My office monitor is a 19 inch Dell LCD, my home is a 15 inch Dell and my laptop is a 10.6 inch wide screen Fujitsu. The server machine has an NVIDIA Geforce 7600 using the restricted drivers. I have compiz desktop effects disabled.

If I login in from my office (with the largest monitor), and then go home, the local session is trying to use the high resolution of the large monitor. In other words, the screen is bigger than the monitor and things are off screen. If I use the laptop to login, I can't use a resolution that is different than the server (like full screen) or I total mess things up. By that I mean, I can't log off NX and then log back on, all I get is a black screen. It gets worse, after that, if I try to start a local session on the server machine and my video is completely messed up, I only get the default background color and a cursor that is clearly stretched with the wrong resolution. The only way I can log to a gnome session is to reboot, ctrl-alt-backspace brings me back to the login screen, but logging on again gives the same results. Even worse, all other user accounts are similarly screwed if they try to log on. (currently logged on users are fine as long as they don't long out). This all happens when I terminate the session, not continue a suspended session, I haven't attempted that.

It seems that the NX server is trying to apply screen resolution to sessions started from different locations which sucks since the clients are so different. 

Any help would be greatly appreciated.

---

### Post by markdjones82 on 2007-10-20
Wish I could help you, but I am having the same issue.  It only happens when i suspend a session though.  I get black screen on the client and on the server machine my session is just hte background and I can't do anything.  I usually need to reboot the machine.  

If I terminate the session I can login just fine.

I am currently using freenx and the nomachine 1.5 client.

---

### Post by rdoolen on 2007-10-22
I have found a workaround that at least keeps me from having to reboot.

I log on to a terminal session and remove the contents of /tmp.

Then when I logon to a gnome session. It works fine.

I doubt this will help you unfortunately because you are trying to continue a session.

---

### Post by jmcantrell on 2007-10-23
upgrading to gutsy broke my NX installation, as well. i am using the latest version from nomachine, nx free edition (not freenx). i'm not having any resolution issues, but half of my gnome applets (including trash, volume control, window list, etc) crash, asking me to delete them from my configuration. i've tried removing my gnome configs (thinking that it may be an incompatibility between gnome versions).
i realize that the packages available from nomachine say that they are for feisty, but it's a shame that they've stopped working. i am basically unable to access my machine the way i would like to (i can still ssh, but that limits some things).

anyone have any idea when nomachine may be releasing an official version for gutsy? doing so may not fix these problems, but it's a start.

---

### Post by jmcantrell on 2007-10-23
just thought i would post an update... clearing out /tmp appears to have corrected my problems with the applets crashing. i will have to wait until i get home to see how local logins work.

---

### Post by rdoolen on 2007-10-23
I discovered the same solution, its a pain, but it works.

I think I am going to put rm -r -f /tmp/* in my .bashrc or .bash_profile

---

### Post by jmcantrell on 2007-10-24
more updates... when i got home and logged in locally, the applets began crashing again

---

### Post by Bellesarius on 2007-10-24
I've got a fresh install of 7.10 and the freenx packages for 7.04... when I run nxsetup --install I get.

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Error: Invalid value "APPLICATION_LIBRARY_PRELOAD=/usr/lib/libX11-nx.so.6.2:/usr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so:/usr/lib/libXcompext.so.1:/usr/lib/libXrender-nx.so.1.2"
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=/usr/bin/dbus-launch --sh-syntax --exit-with-session startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_GNOME=/usr/bin/dbus-launch --sh-syntax --exit-with-session gnome-session"
         Users will not be able to request a Gnome session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.

  Errors occured during config check.
  Please correct the configuration file.

When I attempt to connect from the nx client (1.5) it authenticates, shows a black window with the NX splashscreen and then tanks.

Ideas?
Sean

---

### Post by rdoolen on 2007-10-24
Sounds like your issues are bigger than mine.

I'll post anything that might be helpful.

---

### Post by Evil Robot on 2007-10-25
I have the same problem - I try to connect via Windows NX client to my headless Ubuntu machine - no happy juice (connection dropped after authentication and the NX Machine logo appears). nxserver --start says:

wilsona6@polymorph:~$ sudo nxserver --restart
NX> 100 NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 123 Service stopped
NX> 122 Service started
NX> 999 Bye

What the hell is going on and how can I fix it? This really sucks :(.

Oh yeah, client log:
Info: Proxy running in client mode with pid '3988'.
Session: Starting session at 'Thu Oct 25 04:30:27 2007'.
Warning: Connected to remote version 2.1.0 with local version 3.0.0.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using image cache parameters 1/1/65536KB.
Info: Using pack method '16m-rle-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Forwarding multimedia connections to port '6000'.
Session: Session started at 'Thu Oct 25 04:30:27 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Terminating session at 'Thu Oct 25 04:30:28 2007'.
Session: Session terminated at 'Thu Oct 25 04:30:28 2007'.

---

### Post by rdoolen on 2007-10-25
Evil Robot. It looks like you are trying to log on to a 2.5 server with a 3.0 client. I would try using matching versions.

---

### Post by Evil Robot on 2007-10-25
> **rdoolen said:**
> Evil Robot. It looks like you are trying to log on to a 2.5 server with a 3.0 client. I would try using matching versions.

How can you tell that? And what would I do to upgrade versions?

---

### Post by jmcantrell on 2007-11-06
i noticed that nomachine now has their packages labeled as being for gutsy, although the version numbers are the same. i suspect that the problem is actually with gnome, because kubuntu with nomachine works perfectly.

---

### Post by lunatic77 on 2007-11-10
I too am having problems with Nomachine's NX after upgrading to Gutsy.  I'm not sure if the issue is client-related or server-related.  My client is running on a Macbook if that helps.  This is what I get in the "Detail" box when the client fails to establish a session:

```

NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '518'.
Session: Starting session at 'Sat Nov 10 12:29:03 2007'.
Error: Can't determine the location of the X display socket.
Error: Error 2 'No such file or directory' checking '/tmp//.X11-unix'.
Session: Session terminated at 'Sat Nov 10 12:29:03 2007'.
```

BTW I have uninstalled (and purged) NX and reinstalled just today to see if anything changed, but I get the exact same error message.

Thanks in advance for any help on this issue!

---

### Post by lunatic77 on 2007-11-10
> **lunatic77 said:**
> I too am having problems with Nomachine's NX after upgrading to Gutsy.  I'm not sure if the issue is client-related or server-related.  My client is running on a Macbook if that helps.  This is what I get in the "Detail" box when the client fails to establish a session:

```

NXPROXY - Version 3.0.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '518'.
Session: Starting session at 'Sat Nov 10 12:29:03 2007'.
Error: Can't determine the location of the X display socket.
Error: Error 2 'No such file or directory' checking '/tmp//.X11-unix'.
Session: Session terminated at 'Sat Nov 10 12:29:03 2007'.
```

BTW I have uninstalled (and purged) NX and reinstalled just today to see if anything changed, but I get the exact same error message.

Thanks in advance for any help on this issue!
Well, I believe I just confirmed this is a client issue.  I logged into my NX server from a Debian machine with no problems.  Also I just realized I had never logged into an NX server from my Macbook.  Must be a bug in the newest Mac OS X client???

Has anyone else logged into an NX server with an Intel Mac client successfully?

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

