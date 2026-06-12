---
title: "Help with VNC access"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by ryan179 on 2015-08-23
Hi everyone,

Apologies for my n00b message, but I'm new to Ubuntu and am facing the challenge of getting it all to work!

I'm running Ubuntu Gnome on my media server, and I would like to set up a way to remote access into it from my Mac OSX.  Whether this is done through VNC, RDP, or something else I don't mind; but I've tried a few things that haven't worked and at the moment I'm trying to get VNC to work.  

I have (I think) installed VNCServer onto my Linux server, and am able to run the following commands which lead me to believe I've done it at least partially right:
[LIST]
[*]Service VNCSERVER Stop (works OK)
[*]Service VNCSERVER Start (works OK); "VNC server is already running as :1"
[/LIST]

However, I'm not sure whether I've got the rest of it set up correctly.  Specifically, when I try to log in using VNC Client on my Mac it doesn't work:
[LIST]
[*]192.168.0.2:5900 (I've also tried 5901 and 5902)
[LIST]
[*]On 5900: "Unable to connect to VNC Server using your chosen security setting. Either upgrade VNC Server to a more recent version from RealVNC, or select a weaker level of encryption."
[*]On 5901/5902: "The connection was refused by the host computer"
[/LIST]
[/LIST]

I recognize that there is likely additional detail that you need to understand what aspects are malfunctioning here, so if you let me know what you need (and ideally how to find it!) I'll come back to you right away.

Thanks in advance for the help!

Ryan

---

### Post by TheFu on 2015-08-23
Can you just use ssh for remote connection? You need ssh anyway.  Last time I looked at OSX, they called "ssh" something else. 

Perhaps they call VNC something else too? Is a remote desktop really needed?  BTW, a heavy desktop like Unity (the default in Ubuntu) doesn't work well (if at all) for remote desktop needs.  Most people run something lighter like LXDE or XFCE for that.

---

### Post by ryan179 on 2015-08-23
As I mentioned above, I'm new to this but said I could use any type of remote connection.  However, I would need help getting started on SSH.

Perhaps you can help me out by giving some guidance as to how I'd go about correctly setting up SSH on my Linux Server?

BTW:  I should add that I need a _graphical_ interface, not just command-line access.

---

### Post by steeldriver on 2015-08-23
What "VNCServer" exactly did you install, and how? What is your end goal? Do you want to share the desktop of the physical console, or run an additional independent session via VNC? What VNC client is used on the Mac?

I'm not sure what is included/enabled by default with the Gnome (as opposed to Unity) desktop, however you may already have the Vino "Desktop Sharing" VNC server installed - and possibly already running. That might jive with the fact that you apparently get a refused connection on 5900 even though the VNCServer startup message indicates that it is starting on display :1 (which would normally correspond to port 5901)

Perhaps we should start by looking at exactly what VNC server processes and ports are running / listening:

```

ps -ef | grep -Ei '[v](nc|ino)'

sudo netstat -nlpt | grep -Ei '[v](nc|ino)'

```

on the server

---

### Post by ryan179 on 2015-08-23
Hi Steeldriver,

Thanks for your time and help.

My server is not hooked up to a monitor display, so what I want to achieve is being able to "view" my server's desktop (ie, all applications, files, run maintenance, etc) off my laptop (Mac OSX).  Effectively, I want a Remote Desktop Login so that I can access my Linux server remotely but from within my LAN.

Honestly - I'm not sure what VNCServer's I installed or how I did them; I tried a few different methods I read about online.

I have run your 2 commands above, but you're going to need to help me interpret them!

media@media-pc:~$** [COLOR=#ff0000] ps -ef | grep -Ei '[v](nc|ino)'[/COLOR]**
media+  1137     1  0 08:22 ?        00:00:00 Xtightvnc :1 -desktop X -auth /home/media/.Xauthority -geometry 1024x768 -depth 16 -rfbwait 120000 -rfbauth /home/media/.vnc/passwd -rfbport 5901 -fp /usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb -localhost
media+  1839  1323  0 08:22 ?        00:00:00 /usr/lib/vino/vino-server --sm-disable

media@media-pc:~$ [COLOR=#ff0000]**sudo netstat -nlpt | grep -Ei '[v](nc|ino)'**[/COLOR]
[sudo] password for media: 
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      1137/Xtightvnc  
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      1839/vino-server
tcp        0      0 127.0.0.1:5901          0.0.0.0:*               LISTEN      1137/Xtightvnc  
tcp6       0      0 :::5800                 :::*                    LISTEN      1839/vino-server
tcp6       0      0 :::5900                 :::*                    LISTEN      1839/vino-server

Let me know what next..... or any alternate suggestions you may have.

Note to TheFu above:  I am able to SSH into my Linux Server from my Mac terminal, but this is command-line only and while I can see files, it's not quite what I want to achieve.

Thanks again,
Ryan

---

### Post by steeldriver on 2015-08-23
I'm still not clear whether you are looking for a shared session (think remote help) or independent session (allowing you to  use/administer the remote server while another user is concurrently logged in to their own separate desktop session)

Based on your command outputs you appear to have both:

(1) you have the default "Desktop Sharing" vino-server running and listening on port 5900. I'm not familiar with Mac VNC clients but possibly the only reason you can't connect to that is encryption: this has been a common stumbling block in recent versions and you might want to try disabling it with

```

gsettings set org.gnome.Vino require-encryption 'false'

```

and then trying to connect on port 5900 again.

(2) Xtightvnc server is running on a separate display :1 (port 5901) however it is invoked with parameter -localhost which is causing it to only listen on the loopback interface:

```

**127.0.0.1**:5901

```

 This is a sensible security measure which effectively forces the client to connect via a (secure) SSH tunnel - since you're not doing that, you are getting a "connection refused".

I suspect that (1) is what you really want: try disabling the require-encryption and see if that works for you. If so you can forget about VNCServer.

Either way, PLEASE ensure that you are doing all of this behind a router that blocks ports 59xx from the big bad internet - at least until you have figured out SSH tunnelling.

---

### Post by ryan179 on 2015-08-24
Hi Steeldriver,

Thanks again.  

You are correct that (1) above is what I need: a shared session.  Consequently, I have gone with your code suggestion above and connecting now via VNC through Vino [COLOR=#006400]**DOES WORK! **[/COLOR]Thanks.

I have a couple outstanding questions:

1) How do I disable xtightvnc server now that I seemingly don't need it any more?
2) This may be reason to create a new thread, but here's my issue:  When I log into my Linux machine from my Mac using VNC Viewer, while the "resolution" appears OK, about 80% of the content of the remote desktop is chopped off.  You can see what I'm referring to in the screenshot link below.  Note - there isn't a way to adjust this from within VNC Viewer application (ie, adjusting the size only adjusts the size of the whole VNC window and scales the content).  Further to this (and I'm not sure if it's related), when I plug my server into my old TV screen via HDMI, I have a similar issue where about 50% of the screen is cut off.  However, if I open Kodi (the primary use of my server through my TV), the screen is 100% OK.  I thought this was just an issue with my old TV as there are no issues if I try my friend's newer TV screen, but since the issue seems similar to what happens when I connect via VNC I thought I'd share.  Screenshot of VNC running on OSX:  [http://postimg.org/image/aqd4vok5x/](http://postimg.org/image/aqd4vok5x/)

Thoughts?

Cheers
Ryan

---

### Post by TheFu on 2015-08-24
VNC screens are 100% virtual. Sizes don't have anything to do with hardware.  Last time I used VNC, the resolution desired was set on the command line when starting the server.
```

/usr/bin/vncserver -geometry 1280x752 -depth 24 &
```

Don't know anything about vino.

BTW, have you looked at **x2go**?

---

### Post by steeldriver on 2015-08-24
1) unless you scripted it to autostart somehow, you can simply stop the vncserver and not restart it

```

vncserver -kill :1

```

You can check that it's stopped using the same 'ps' and/or 'netstat' commands as before. You could remove the tightvncserver package if you want.

2) I have no Mac experience but that looks to me like something you would need to fix on the Mac VNC viewer (display scaling?)

---

### Post by ryan179 on 2015-08-24
1) I may have through the various tutorials I tried set VNCServer to start automatically.  Can you tell me how to check that it's not auto starting?

2) I don't think this is a specific Mac issue:  I have tried 2 different VNC clients (on both Windows and Mac), and they both have the same issue.  There are no settings at all which will adjust the size of the embedded virtual desktop.  I do believe this is an issue with the server-side Linux / Vino setup.  Any other thoughts on how I can explore this?  Is this a limitation with Vino?

Thanks

---

### Post by TheFu on 2015-08-24
I didn't see any resolution or scaling controls for vino. Could have missed them.

[https://askubuntu.com/questions/52556/headless-machine-increase-remote-desktop-resolution](https://askubuntu.com/questions/52556/headless-machine-increase-remote-desktop-resolution) 

They definitely exist with other options like ... NX via x2go.

---

### Post by brad-bogar on 2015-08-25
> **ryan179 said:**
> 1) I may have through the various tutorials I tried set VNCServer to start automatically.  Can you tell me how to check that it's not auto starting?

2) I don't think this is a specific Mac issue:  I have tried 2 different VNC clients (on both Windows and Mac), and they both have the same issue.  There are no settings at all which will adjust the size of the embedded virtual desktop.  I do believe this is an issue with the server-side Linux / Vino setup.  Any other thoughts on how I can explore this?  Is this a limitation with Vino?

Thanks

I would dump the vnc idea and go with a software based solution that works on both Ubuntu and Mac: Teamviewer. ([https://www.teamviewer.com/en/index.aspx](https://www.teamviewer.com/en/index.aspx)) While, yes it would not provide an open source option it would prevent you from having to do the necessary port forwarding needed to get VNC to work through your home router/modem (the missing step from the above attempts). The program works flawlessly in Windows, Mac, and Linux. Give it a try, once you set it up and have the first email address/password set up, the additional clients you want to add are even easier.

---

### Post by ryan179 on 2015-08-26
brad-bogar,

While this reply doesn't specifically address the resolution issue which persists with Vino, it _is_ a reasonable workaround.

I have TeamViewer working, and the resolution is perfect.  

Thank you.

---

