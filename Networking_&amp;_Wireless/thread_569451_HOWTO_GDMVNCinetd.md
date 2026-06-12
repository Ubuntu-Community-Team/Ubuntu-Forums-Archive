---
title: "HOWTO: GDM/VNC/inetd"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by lns on 2007-10-07
Hey all,

When I followed the steps in: 

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

I noticed that it called for xinetd to be installed. I could not do this, as I require inetd for the LTSP server that was on this machine. Now I know I could create an xinetd for the necessary network daemons required by LTSP, but it seemed backwards to me to do this as its primary function is serving LTSP sessions - and with keeping compatibility with scripts run by LTSP software updates, etc... I just wanted to run Xvnc in inetd. So I did. Here's how I did it:


1 ) Enable XDMCP
- System->Administration->Login Screen Setup
- Tab Remote -> Style = "Same as local"
- Bottom button XDMCP (still in Remote) --> You can disable "Honor Indirect Requests" if you'd like.

2 ) Add all Ubuntu universe/multiverse repositories via Synaptic Package Manager or by manually editing /etc/apt/sources.list

3 ) Install vnc4server (and openbsd-inetd if it's not there already):
```
$ sudo apt-get install vnc4server openbsd-inetd
```

4 ) Add following to /etc/inetd.conf:

```
5901    stream    tcp  nowait root  /usr/bin/Xvnc Xvnc -inetd :1 -query localhost -geometry 800x600 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared securitytypes=none -extension XFIXES
```

Note 1) You can add as many Xvnc servers for simultanious, seperate VNC/GDM sessions by adding another line to /etc/inetd.conf, simply increasing the port number and display number in the line by one, for example:

2nd VNC session (port 5902, display :2):
```
590**2**    stream    tcp  nowait root  /usr/bin/Xvnc Xvnc -inetd :**2** -query localhost -geometry 800x600 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared securitytypes=none -extension XFIXES
```

3rd VNC session (port 5903, display :3):
```
590**3**    stream    tcp  nowait root  /usr/bin/Xvnc Xvnc -inetd :**3** -query localhost -geometry 800x600 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared securitytypes=none -extension XFIXES
```

..etc, etc etc....

Note 2) that this does not ask for the root VNC password before connecting. I am using this in a secure LAN environment so I don't mind people logging into a login prompt without a password. You can always put the original switch in ( 
passwordFile=/root/.vncpasswd ) if you want to retain the VNC password functionality.

5 ) Restart inetd with:
```
$ sudo /etc/init.d/openbsd-inetd restart
```

6 ) Bookmark this page, as we will be logging out and logging back in.

7 ) Log out of Gnome. When you get to the GDM screen, hit CTRL+ALT+BACKSPACE. This will restart the GDM service (required).

8 ) Log back in and test locally with:
```
$ vncviewer localhost:1
```

9 ) Test remotely with:
```
$ vncviewer <ipaddress>:1
```

----
**BONUS: ADD REMOTE SSH TUNNEL TO ENCRYPT VNC SESSION:**

*Prerequisite: You must have sshd running on the server already - this step is outside the scope of this post.*

1 ) From the client (assuming it is also Ubuntu Linux), connect to the remote SSH service using the -L (port-forwarding) switch:

```
$ ssh -L 5901:127.0.0.1:5901 myusername@<public_remote_ip>
```

Note: Obviously, substitute the forwarding port match the display you're trying to connect to via VNC.

After you log in via SSH, fire up a VNC viewer session (on your local machine) to the remote server using LOCALHOST:1 which forwards local port 5901 over SSH to the remote server port 5901 (again, remember to substitute :1 with whatever display you're trying to connect to):

```
$ vncviewer localhost:1
```
---

Have fun with this! SSH seems to compress VNC traffic pretty well, not to mention make it SECURE over untrusted networks (I.E. the Internet)!

---

### Post by xxbill420xx on 2008-02-01
Thanks for creating and publishing this tutorial.  With the problem's I've been facing this gives me some more options to play around with.  Currently I'm searching on google to see if I can enable XDMCP and the options you have listed at the top.  I am guessing that those options also have something to do with the '/etc/init.d/openbsd-inetd restart' command, because  I try running that and it says command not found... should I try maybe just inetd??
```

nimda@nimda-server:~$ sudo /etc/init.d/openbsd-inetd restart
sudo: /etc/init.d/openbsd-inetd: command not found

```

Also I am unable to locate the  /etc/X11/gdm/gdm.conf file... so that probably is also tied into the first thing you have us enable from the Administration menu about XDMCP.  This is a computer I have already used with a monitor so I know its window system is up and running with gnome working perfectly.

---

### Post by lns on 2008-02-01
> **xxbill420xx said:**
> Thanks for creating and publishing this tutorial.  With the problem's I've been facing this gives me some more options to play around with.  Currently I'm searching on google to see if I can enable XDMCP and the options you have listed at the top.  I am guessing that those options also have something to do with the '/etc/init.d/openbsd-inetd restart' command, because  I try running that and it says command not found... should I try maybe just inetd??
```

nimda@nimda-server:~$ sudo /etc/init.d/openbsd-inetd restart
sudo: /etc/init.d/openbsd-inetd: command not found

```

I *thought* inetd is installed by default - I might be wrong. I know it always is on my LTSP installs (which are all Ubuntu Gutsy installs) - and that's what the init script is called. Try looking at the scripts and see if it's named something else - otherwise just install it.

> Also I am unable to locate the  /etc/X11/gdm/gdm.conf file... so that probably is also tied into the first thing you have us enable from the Administration menu about XDMCP.  This is a computer I have already used with a monitor so I know its window system is up and running with gnome working perfectly.

Actually it's /etc/gdm/gdm.conf - I'll verify my post reflects this. Thanks!

---

### Post by xxbill420xx on 2008-02-01
Ahh yes well more progress thanks for the information once again.  So I messed around inside of that gray vnc console with nothing but the terminal open.  I have found that I can launch my X window applications and it works!  This is exactly what I wanted, and when I close out... it keeps the session open, also good! 

So now what I need to figure out, is if theirs anyway to make my normal menus and things appear as if was logging in at the screen.  Do you know anything about Nautilus, I thought that had something to do with the interface setup.  When I launch applications such as Konsole or gnome-terminal, they work great in every way..  only they dont have the bar up at the top that usually has the window functions (minimize, close, etc) and I cant drag the windows to move them, so they end up stacking on top of each other.  Any ideas what I might need to launch to start that up?  

Thanks

*****Okay i solved the problem... the issue i was having was that when i logged in I was receiving the gray screen a single root console in the upper left corner.  The console had no interface properties at all i couldn't right click anything.  There were no borders to move windows, it would execute windows applications tho, those however also have no borders. To solve this, I typed exec gnome-session
and it launched everything i wanted as if i was right at the screen.  Hope this helps someone, thanks for your assistance as well.

---

### Post by vertical98 on 2008-02-03
Thanks, got it to work right out of the box.

---

### Post by awright418 on 2008-04-18
This worked perfectly for 8.04 if anybody is looking for a solution like I was. Now I need to figure out how to just boot to the terminal when the desktop is installed. Any ideas?

---

