---
title: "How to connect to VNC using SSH?"
date: 2019-11-05
forum: Networking &amp; Wireless
---

### Post by techcomputerworld on 2019-11-05
my problem is that I need a reverse ssh to connect from my pc to the server with Kubuntu 18.04.3 and there is no way it works I have tried this and it does not work

[https://www.techrepublic.com/article/how-to-connect-to-vnc-using-ssh/](https://www.techrepublic.com/article/how-to-connect-to-vnc-using-ssh/)
I've tried the link but don't run.

---

### Post by TheFu on 2019-11-05
Please be EXTREMELY clear about your setup, what the client is, what the server is, the exact ssh tunnel command used, etc.  If ssh between the client and the server doesn't work, then no way will trying to get VNC through a tunnel work.  

BTW, most companies don't allow ssh from the outside into desktops, so you can only use their VPN to gain access.

---

### Post by techcomputerworld on 2019-11-06
Hi, thanks for your help! I don't know because I failed the connection yesterday, but I tried again and it works.
I am using TigerVNC for server.
TightVNC Viewer to see the server desktop.
To connect to the server I have to do the command
ssh -L 5901: localhost: 5901 onzulin@192.168.1.246 or this other
using certificate
ssh -L 5901: localhost: 5901 kubuntu
configured in /.ssh/config.
Then run the TigerVNC server
vncserver -geometry 1920x1080 -depth 24
that puts it in me: 1
With this other command:
$ vncserver -list

TigerVNC server sessions:

X DISPLAY # PROCESS ID
: 1 1322
All this yesterday did not work and that's why I asked.
Is it possible to put the TigerVNC Server as a service that starts with Ubuntu startup and then just have to do the tunnel every time I say connect? Regards.

---

### Post by slickymaster on 2019-11-06
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2019-11-06
First, be very careful about adding spaces where they aren't allowed and not having spaces where they must be.  It matters.

Second, if you want a fast, encrypted, remote desktop that is easy to use and only goes over the ssh port configured in the ~/.ssh/config file for each different system, use x2go.  To me it feels 2-3x faster than any VNC.  We have control over the bandwidth targets, compression levels, etc with x2go.  Authentication uses ssh-keys, if you already have those setup.  Much easier than hacked together VNC stuff.

---

