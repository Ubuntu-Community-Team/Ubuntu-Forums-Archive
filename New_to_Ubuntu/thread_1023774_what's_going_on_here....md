---
title: "what's going on here..."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by marcusesses on 2008-12-28
So I was attempting to run a script that would launch rhythmbox using cron at a specific time. 

[http://ubuntuforums.org/showthread.php?t=1023584](http://ubuntuforums.org/showthread.php?t=1023584)
(This thread is still ongoing).

Like I mention in that thread, the script works fine when I run it manually, but when the script is run by cron, I get an error that says:

"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-dgQWOXy5Uo: Connection refused)"

Now, when starting up my computer, when it initially boots up (after I've logged in), I get an error that says somehting like:

"Failed to contact configuration server for Encryption Key agent (Seahorse)"

(MORE: "Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-zCbQ8NeYZI: Connection refused)")

then after some time

""Failed to contact configuration server (X-session manager)"
and finally
"Failed to contact configuration server (gnome settings daemon)".
On that last one, when I look at details, it says
"failed to connect to socket /tmp/dbus-7o0BVnK1Vq: connection refused.

As these error windows were opening, it took forever to load (think windows), and as you would expect, the gnome settings are all wonky (text for applications on my desktop are all different sizes, my Firefox window is a different color,volume is automatically muted and I can't adjust the volume using the external volume control...there are probably other things too...).

Does anyone have any idea what's going on here? Thanksk in advance

---

### Post by blueridgedog on 2008-12-28
Was your system up and running at the time specified?  It almost appears that the script ran when X was not running (guessing).

---

### Post by blueridgedog on 2008-12-28
Perhaps, try and run your script without the display export (reboot to resolve the misdirection of the display).

---

### Post by marcusesses on 2008-12-28
> Was your system up and running at the time specified? It almost appears that the script ran when X was not running (guessing).

I'm not sure I see what you're saying. But to test that the script worked, I would change the time to 1 or 2 minutes from the current time. So the system was always running at the times I specified. 


> Perhaps, try and run your script without the display export (reboot to resolve the misdirection of the display).


This didn't do too much. I would also need to use X to run display the application (rhythmbox).

I updated yesterday; I'm running ubuntu 8.04, and I ran a apt-get update yesterday. I think this might have something to do with it (can anyone confirm this? Are there any bugs in the 8.10 updates?)

The only other things I did were put items in the crontab, so I'm not sure where theses errors would surface from.

---

### Post by blueridgedog on 2008-12-28
Perhaps you could start your script with an

xhost +

and end it with 

xhost -

Letting your local X server accept the display.  Perhaps the upgrade altered your X.hosts file.

---

### Post by marcusesses on 2008-12-28
> **blueridgedog said:**
> Perhaps you could start your script with an

xhost +

and end it with 

xhost -

Letting your local X server accept the display.  Perhaps the upgrade altered your X.hosts file.
Still didn't work with cron. When I started manually, it produces this message
```
access control disabled, clients can connect from any host
access control enabled, only authorized clients can connect
```

But it works anyway. I still think it has something to do with the updates. Before I ran them, it wasn't working, but it at least had the decency to show an error message

```
An error occured while loading or saving configuration information for rhythmbox. Some of your configuration settings may not work properly.

Details:

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details - 1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-dgQWOXy5Uo: Connection refused)
```

I get similar errors when I reboot, so the problems are probably related, but I'm at a loss as to what could be wrong...

(another post I made last night, related to this post: [http://ubuntuforums.org/showthread.php?t=1023584](http://ubuntuforums.org/showthread.php?t=1023584))

---

### Post by blueridgedog on 2008-12-28
Well, at least we verified that it is not an issue with the display export as your x server was open to all during the script.

---

### Post by marcusesses on 2008-12-29
Right...so now when I log in I get the errors I mentioned in the OP, but now I'm getting the white screen of death!

When I ran the update, I think something went wrong...did I update something accidently? I've heard that some people somehow updated their kernel when they ran updates...is this a possibility?

Anyone have any idea what's going on here???

Is there any information that would clear up the issue? Anyone had a similar problem or familiar with this? 
Thanks...

I also ran this command

```
dpkg-reconfigure -phigh xserver-xorg
```
and got the same thing...so the problem isn't there...

---

