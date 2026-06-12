---
title: "Starting VNC over SSH"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by shortridge11 on 2008-09-10
I've checked out the other posts relating to this topic and tried them, and they did not work.  I have a headless machine- a box with no monitor- and i want to be able to get into it's gui.  I tried typing
sudo startx

and the output is 

xauth: (stdin):2:  unknown command "64cbdf51d1a2090817f15620877a19b5"
xauth: (stdin):3:  unknown command "64cbdf51d1a2090817f15620877a19b5"

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Then i downloaded x11vnc because someone told me i needed that for the x session to start properly.  Afterwards i just typed in
vncserver

and it said it would output

New 'X' desktop is xxxxxxxxx:1

Starting applications specified in /home/xxx/.vnc/xstartup
Log file is /home/xxx/.vnc/xxxxxxxxxxx:1.log

then when i tried getting into the session, it was unable to connect to host.  I tried

vncviewer xxxxxxxxx.net :1

and it said unable to connect to host: Connection refused(111)

I've tried many different ways of getting vnc to work over ssh, but it's just not working and i'm unsure why.  Can someone help me solve this problem?

---

### Post by cb951303 on 2008-09-10
uhm I'm not an expert on the issue but AFAIK ssh does not support what you're trying to do. What you want is to install and run a VNC server on the headless machine and then run a VNC client and connect to the headless machine on your other box. AFAIK that has nothing to do with ssh

---

### Post by shortridge11 on 2008-09-10
i was using vncserver.  Isn't that a vnc server? I guess i'm just not understanding why this won't work =\

---

### Post by cb951303 on 2008-09-11
yeah but than you login to the headless computer with ssh, it's not right. you should connect to the headless computer directly form a vnc client

EDIT: there is a program in ubuntu standard installation called "Remote Desktop Viewer" under Menu>Internet (it may be hidden though) It's a vnc client. Use that. You have absolutely nothing to do with SSH

---

### Post by shortridge11 on 2008-09-11
i ssh in to start the vnc server via
vncserver

It then tells me that the new 'X' desktop is xxxxx:1

i then try to vnc into my box using

vncviewer xxxxxxx.net :1

and it says unable to open display.  Why can't i vnc into my box? =\

---

### Post by cb951303 on 2008-09-11
try using Remote Desktop Viewer. it has the ability to look for vnc servers on your lan. If it doesn't show there, there must be something wrong with the server configuration.

---

### Post by shortridge11 on 2008-09-11
I'm not connected to the lan.  I'm connecting to my ip and my router is forwarding the port.  And when i'm connected to my lan or i connect to my vpn, it still can't see it.  Do you know what could be misconfigured?

---

### Post by cb951303 on 2008-09-11
:\ sorry, it could be a simple router problem though. Are you sure the headless machine is accessible by outside?

---

### Post by shortridge11 on 2008-09-11
i ssh into it. The port is forwarded, it's really weird.  This is the part that confuses me.  When it's plugged into a monitor (VGA) then i can vnc into it.  When it's headless and doesn't have anything plugged into it, then i can't get vnc to work.

edit- the reason i say i ssh into it is to show that it's up and actually running.  I am not trying to imply that ssh is vnc, or anything of the like

---

### Post by iwein on 2008-09-28
> **shortridge11 said:**
> i ssh into it. The port is forwarded, it's really weird.  This is the part that confuses me.  When it's plugged into a monitor (VGA) then i can vnc into it.  When it's headless and doesn't have anything plugged into it, then i can't get vnc to work.

edit- the reason i say i ssh into it is to show that it's up and actually running.  I am not trying to imply that ssh is vnc, or anything of the like

I get the point, because I have the exact same problem. It puzzles me that all howto's seem to assume you have a monitor connected to your server. Not really the setup I would recommend for a server.

Possibly I'm not l33t enough to have a server at all ;)

---

