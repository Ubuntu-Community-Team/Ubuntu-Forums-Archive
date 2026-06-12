---
title: "[SOLVED] Need Help getting VNC working ?"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2007-11-20
I followed [this post](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html) ([http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)) to the 'T'... I also read thru this thread [HOWTO: Set up VNC server with resumable sessions](http://ubuntuforums.org/showthread.php?t=122402)

And I am pretty sure I did everything right, except when I try and connect from my WinXP box using TightVNC I get the following error message:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/ScreenShot28.jpg[/IMG]
Any ideas?
Thanks again,
-BassKozz

---

### Post by BassKozz on 2007-11-21
Since I haven't heard anything I went ahead and installed UltraVNC and RealVNC to see if I might have better luck with one of those clients, here are the results...

[CENTER][SIZE="5"]**_UltraVNC_**[/SIZE]

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/UltraVNC1.jpg[/IMG]
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/UltraVNC2.jpg[/IMG]:(
[SIZE="5"]**_RealVNC_**[/SIZE]

[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/RealVNC1.jpg[/IMG]
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/RealVNC2.jpg[/IMG]:([/CENTER]

I can't figure out for the life of me what I am doing wrong here... I am trying to connect to the box on my local LAN, but I setup port forwarding anyways and tried to connect via my WAN IP address and got the same results.  On another note, I was able to get Xming working perfectly, but I can't get an answer on [whether or not I can use Xming as a "Full Desktop Environment"/VNC replacement](http://ubuntuforums.org/showthread.php?t=619611)?

---

### Post by BassKozz on 2007-11-21
[DELETE - mistake double post]

---

### Post by BassKozz on 2007-11-22
Please someone help me here... I can't even do a simple VNC connection from the actual machine I am on ```
vncviewer localhost:1
``` it gives me a ```
CConn:       connected to host localhost port 5901
 main:        read: Connection reset by peer (104)
```
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/VNC-104error.png[/IMG]:(

PLEASE SOMEONE HELP :frown:

---

### Post by BassKozz on 2007-11-25
:bump:
Still Lookin for help here

---

### Post by BassKozz on 2007-11-25
:bump:
no one wants to take a stab at this?

---

### Post by BassKozz on 2007-12-13
Still Not Working...](*,)
Please Help

---

### Post by lordnacho on 2007-12-13
I have the same issue.  The bundled VNC was working, but I wanted to go headless and not login locally, so I tried to install vnc4server.  Didn't work, even tried the Edgy version as I read the Feisty version was buggy(even though I'm on Gutsy)

Anyone know what this problem is?

---

### Post by BassKozz on 2007-12-14
WORKING :D
Thanks to this: [http://ubuntuforums.org/showthread.php?p=236053](http://ubuntuforums.org/showthread.php?p=236053)

---

### Post by lordnacho on 2007-12-14
B/-\ssKozz,
Seems I couldn't connect to the :1 instance, but if I started another one using:
vnc4server

It would start a new one <hostname>:2 and I could connect to that one, both locally using localhost and across the network by hostname or Ip address.

Hope that helps a bit.  I'll have to play more with it

---

### Post by lordnacho on 2007-12-14
You beat me :)

I'll take a look at your link later.  Gotta hit the hay now

Thanks

---

### Post by BassKozz on 2007-12-14
> **lordnacho said:**
> B/-\ssKozz,
Seems I couldn't connect to the :1 instance, but if I started another one using:
vnc4server

It would start a new one <hostname>:2 and I could connect to that one, both locally using localhost and across the network by hostname or Ip address.

Hope that helps a bit.  I'll have to play more with it


> **lordnacho said:**
> You beat me :)

I'll take a look at your link later.  Gotta hit the hay now

Thanks

Confused???:confused:
Beat you at what?
I followed this HowTo: [http://ubuntuforums.org/showthread.php?p=236053](http://ubuntuforums.org/showthread.php?p=236053)
And I was able to access my local desktop connection ":0", I am not sure how to create a new session with this method, but thats fine because I am not trying to create a new session anyways ;)

---

### Post by lordnacho on 2007-12-14
Your post beat my post by 2 seconds, both at 12:09 AM :)

I'm still trying to create a new session, as I'm going to run headless and will not be able to auto login the :0 session.

---

### Post by BassKozz on 2007-12-14
> **lordnacho said:**
> I'm still trying to create a new session, as I'm going to run headless and will not be able to auto login the :0 session.

You can "auto login", check this out: [http://ubuntuforums.org/showthread.php?t=45565&p=3949181](http://ubuntuforums.org/showthread.php?t=45565&p=3949181)
and read thru the thread.

---

### Post by lordnacho on 2007-12-15
Thanks, but got mine working.  Tweak the server_args a little and it worked

---

### Post by BassKozz on 2007-12-15
> **lordnacho said:**
> Thanks, but got mine working.  Tweak the server_args a little and it worked
Can you elaborate on what you tweaked?
I am still trying to set it up so that it's automated, right now I have to manually run the following command via SSH, everytime I want to logon (if I haven't already logged onto my user/machine locally):
```
sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display :0
```

---

### Post by lordnacho on 2007-12-16
I haven't added the SSH in yet, but I'm just using it locally. 

So, now it handles one person can be physically logged on at :0 and then one remote :1, I'm not sure how to do x number of instances.  I had a mac and a pc connect to the :1, provided someone wasn't already logged in.  Ran into weird problems if they logged in with the same user as who was logged into :0

I think it might have been a path to my fonts.  Try running  /usr/bin/Xvnc with the server_args on the command line, it should tell you whats wrong.  Just use a new instance in the server_args :2, :3, etc

Here's my /etc/xinetd.d/Xvnc

```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}
```

And /home/<user>/.Vnc/xstartup

```
#!/bin/sh

#xrdb $HOME/.Xresources
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresarouces ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
unset SESSION_MANAGER
gnome-session &
```

Thanks to the many posts I scoured through to learn about this and getting my wifi card working.  Now my ubuntu box is completely headless and running audio cables to my home theater in the living room.  I love Amarok btw :)

---

### Post by HeinekenPissr on 2008-01-27
@ B/-\ssKozz

I have the same problem you did
 "read: Connection reset by peer (104"

I checked out the thread u suggested and tried some of it.  Exactly what from that thread solved your problem?

---

### Post by BassKozz on 2008-01-28
> **HeinekenPissr said:**
> @ B/-\ssKozz

I have the same problem you did
 "read: Connection reset by peer (104"

I checked out the thread u suggested and tried some of it.  Exactly what from that thread solved your problem?

I'll be honest **HeinekenPissr**, I can't remember what it was exactly that I did, it's been a while since I've done it, and I've left it alone since then...
Sorry I couldn't be of more assistance.

---

