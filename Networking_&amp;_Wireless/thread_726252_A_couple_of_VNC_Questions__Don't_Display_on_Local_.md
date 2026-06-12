---
title: "A couple of VNC Questions / Don't Display on Local Monitor + AutoStart + Full Screen"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2008-03-16
I am using Ubuntu 7.10 64-bit, and I can successfully VNC into my box already using TightVNC on my WinBlows Box, but I have a few further questions:

1. When I walk away from my computer my monitors (plural, I am using a Dual Monitor Setup) go into sleep mode after about 10minutes to save power.  But when I login via VNC the monitors come back to life, and display everything I am doing on them remotely (via VNC).  This is not good for 2 reasons: 1. It eats away at electricity, which is unnessesary because I am not sitting in front of the screens, so I don't need them on. 2. Security, I'd rather not have the monitors display what I am doing on my computer while I am away from them...
**So the question is, is there a way to keep the monitors in sleep mode or at the very least a blank/black screensaver when I am connected via VNC?**

2.** How can I setup VNC to auto start on reboots so the I can logon remotely?** Currently in order to logon after a reboot I have to SSH into the box and enter the following:```
sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display :0
```
How can I set this up so that I don't have to send that command before connecting?

3. *(This is a TightVNC question, but I figured I'd ask it here anyways)* **How can I have the my VNC session display in full screen even if the displays aspect ratio's (resolution's) are different?**
For example if I am trying to display my Ubuntu Box (1280x1024) on my XP Laptop (1680x1050) it leaves black bars on the left+right of the screen to fill  in the gaps and keep the aspect ratio the same, but is there a way to have it display the screen fully so that it fills in those gaps?
Example: [[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_VNCfullscreen.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/VNCfullscreen.jpg)

Thanks in advance for any/all comments/suggestions, 
-BassKozz

---

### Post by scorp123 on 2008-03-16
> **B/-\ssKozz said:**
>   1. When I walk away from my computer my monitors (plural, I am using a Dual Monitor Setup) go into sleep mode after about 10minutes to save power.  But when I login via VNC the monitors come back to life, and display everything I am doing on them remotely (via VNC). Use the **tightvncserver** package and use a virtual desktop session, e.g. screen **:1** ... that one would then be completely independent of what is running on screen **:0** (= your real phsyical screen).

Command line example:
**vncserver :1 -depth 16 -geometry 1600x1200**

You then connect using any VNC-compatible client, target has to be specified as:
**remotehost:1**

Or:
**remote.IP.address.here:1**

> **B/-\ssKozz said:**
>  How can I setup VNC to auto start on reboots so the I can logon remotely?  You could put my command above into **/etc/rc.local** ... The key is to use the real VNC server package, not that x11-to-vnc thing. So if you want to execute VNC for a specific user:
**sudo -u yourusername -H 'vncserver :1 -depth 16 -geometry 1600x1200'**

---

### Post by BassKozz on 2008-03-16
> **scorp123 said:**
> Use the **tightvncserver** package and use a virtual desktop session, e.g. screen **:1** ... that one would then be completely independent of what is running on screen **:0** (= your real phsyical screen).

Command line example:
**vncserver :1 -depth 16 -geometry 1600x1200**

You then connect using any VNC-compatible client, target has to be specified as:
**remotehost:1**

Or:
**remote.IP.address.here:1**

 You could put my command above into **/etc/rc.local** ... The key is to use the real VNC server package, not that x11-to-vnc thing. So if you want to execute VNC for a specific user:
**sudo -u yourusername 'vncserver :1 -depth 16 -geometry 1600x1200'**
Yes but then I wouldn't be able to logon to my local session, meaning if I opened up Firefox while I was sitting infront of the computer, I wouldn't then be able to open up firefox when connected via screen:1 because there would already be an instance running on screen:0... correct?

---

### Post by krunge on 2008-03-16
> 
[B]So the question is, is there a way to keep the monitors in sleep mode or at the very least a 
blank/black screensaver when I am connected via VNC?[/B]

Recent versions of x11vnc have -forcedpms and -clientdpms options that may do what you want.

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-forcedpms]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-forcedpms")

I think the -clientdpms is closer to what you ask for.  Neither is really secure since they use DPMS (monitor powersaving).  AFAIK, there is no X API to guarantee blanking of the framebuffer.
> 
2.** How can I setup VNC to auto start on reboots so the I can logon remotely?** 
How can I set this up so that I don't have to send that command before connecting?

There are some ideas here in the 'Continuously' section: 

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

The file locations and names are often distro dependent. Don't forget the GDM KillInitClients=false in gdm.conf and also gdm.conf-custom if you have one.

---

### Post by scorp123 on 2008-03-16
> **B/-\ssKozz said:**
>  Yes but then I wouldn't be able to logon to my local session  **vncviewer localhost:1**

---

### Post by BassKozz on 2008-03-17
> **krunge said:**
> Recent versions of x11vnc have -forcedpms and -clientdpms options that may do what you want.

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-forcedpms]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-forcedpms")

I think the -clientdpms is closer to what you ask for.  Neither is really secure since they use DPMS (monitor powersaving).  AFAIK, there is no X API to guarantee blanking of the framebuffer.

There are some ideas here in the 'Continuously' section: 

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

The file locations and names are often distro dependent. Don't forget the GDM KillInitClients=false in gdm.conf and also gdm.conf-custom if you have one.I'll try this out and report back...
Thanks :D
> **scorp123 said:**
> **vncviewer localhost:1**
:confused: does this allow connection to the local session w/out waking the Monitors from sleep mode?

---

### Post by krunge on 2008-03-18
> **B/-\ssKozz said:**
> 
:confused: does this allow connection to the local session w/out waking the Monitors from sleep mode?

I think scorp123 means that even when you are local to where your vncserver session is (I.e. sitting at the actual box) you use vncviewer to view it. That way you have the same virtual VNC session no matter where you go, even locally you just use VNC to see it.

This is the traditional way VNC was intended for use on Unix.  Some people do it, but I don't think it really caught on: most people want the system default X session locally.

BTW, There is a trick to get this in a naked X session (no window-manager or desktop: you basically make your window manager be vncviewer).

---

### Post by BassKozz on 2008-03-19
> **krunge said:**
> I think scorp123 means that even when you are local to where your vncserver session is (I.e. sitting at the actual box) you use vncviewer to view it. That way you have the same virtual VNC session no matter where you go, even locally you just use VNC to see it.

This is the traditional way VNC was intended for use on Unix.  Some people do it, but I don't think it really caught on: most people want the system default X session locally.
ahh, I see...
> **krunge said:**
> 
BTW, There is a trick to get this in a naked X session (no window-manager or desktop: you basically make your window manager be vncviewer).
You lost me here:confused:
Can you give an example?

---

### Post by krunge on 2008-03-19
> **B/-\ssKozz said:**
> 
You lost me here:confused:
Can you give an example?

In the simplest situation the login manager (usually GDM) will respect whatever you have in the shell script  ~/.xsession.  I don't know if a default setup of ubuntu respects or ignores this file; one would have to check.

So you can have that shell script run any program you want.  It doesn't need to start a Desktop or window manager at all.  So have ~/.xession run vncviewer:
```

#!/bin/sh

vncviewer -encodings raw localhost:1

```
This assumes you have already started the VNC session via```
vncserver :1
```
on that same machine (and, say in the script ~/.vnc/xstartup you have "gnome-session" or "startkde" to start up whatever desktop/windowmanager you want in the vncserver VNC session.)

Newer viewers might need -PreferredEncoding=raw or something.  This is used because for local viewing (vncviewer and vncserver on the same machine) it is fastest to use no compression at all.

Now suppose you had a lot of machines (LAN, WAN, etc) and all mounted your homedirectory by NFS, say.  Suppose the machine you ran "vncserver :1" is named "wombat".  Then you could have this in ~/.xsession:
```

#!/bin/sh

if hostname | grep wombat > /dev/null; then
       vncviewer -encodings raw localhost:1
else
       # could do ssh -L .... wombat stuff here for ssh tunnel, etc.
       vncviewer wombat:1
fi

```
Then no matter which machine you logged into you'd get that same wombat:1 session.

If the screen resolutions varied from machine to machine it might be awkward.  if Xvnc supported RANDR resize extension I guess  you could just resize it at the beginning of each login.

I believe this is how VNC was intended to be used on Unix when VNC was first created about 10 years ago.  I don't think it really caught on. It is a clean solution, but I think people want to have the most graphics speed as possible locally (whether they need it or not) and also avoid the hassle / incompatibilities of using Xvnc instead of the system X server.

---

### Post by scorp123 on 2008-03-19
> **krunge said:**
>  I believe this is how VNC was intended to be used on Unix when VNC was first created about 10 years ago.  According to what I once read on the original creator's homepage (Olivetti Research Laboratory in Cambridge, England) they came up with this because they needed to keep stuff running in the background and they also needed to be able to reconnect to whatever they were running from another machine. VNC can do that tip top: You can open a new VNC desktop session, start something in there (e.g. a compile process or a large file download), leave the session, go somewhere else and then reconnect and check again how your program is doing. You can also share your session with others, or give them "view-only" access (e.g. they can see stuff but not interact with anything).

The problem with classic X11 sessions is this: As soon as you cut the connection the applications will instantly crash and die! This is because of the client+server nature of the X11 protocol. There needs to be an X11 server (e.g. your graphics card's drivers) and there needs to be a client, e.g. a program which is physically stored on a remote machine. To test this:
```
ssh -X username@some.remote.machine '/usr/bin/xclock' 
``` ... This will give you the remote machine's **xclock** program on your desktop. And now pull the cable or hit CTRL+C inside the terminal window where you executed ssh ... Result? **xclock** instantly vanishes. You just killed it.

So once you executed a program via such a connection ...
- you can't just log out and walk away
- you can't just disconnect and reconnect and hope that your application is still alive
- you can't share the session just like that
- you can't connect to the same session from another machine

All this because of the one-to-one "client + server" mapping X11 applications have. 

**VNC remedies all that. **With VNC the roles of client and server are both on the remote machine where the VNC session is ... the program you connect with is just the "VNC viewer". A viewer = It's not part of the "client + server" interaction between X11 graphics driver + X/Windows program. Therefore you can disconnect, reconnect, and disconnect and reconnect again at will ... your application will not die, it will keep running.

=> That's the scenario where VNC indeed has caught on.

> **krunge said:**
>   I don't think it really caught on.  Not in the scenario and in the role you demonstrate (nice one, BTW).

---

### Post by krunge on 2008-03-19
> **scorp123 said:**
> 
=> That's the scenario where VNC indeed has caught on.

Yes, I certainly agree.  I didn't mean to imply VNC never caught on, only the usage mode on Unix where you use vncviewer both locally and remotely to view a single session.

I use and rely on VNC daily in many of the ways you described.  At work we even use a vncserver session at the top of Mauna Kea to control a telescope.

---

### Post by scorp123 on 2008-03-20
> **krunge said:**
>   At work we even use a vncserver session at the top of Mauna Kea to control a telescope. IP address + username + password please? :D

---

