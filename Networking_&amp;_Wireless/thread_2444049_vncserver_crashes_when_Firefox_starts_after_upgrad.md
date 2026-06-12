---
title: "vncserver crashes when Firefox starts after upgrade to 20.04"
date: 2020-05-23
forum: Networking &amp; Wireless
---

### Post by madbrain on 2020-05-23
I upgraded my home NAS from 18.04 to 20.04 . 

The vncserver now crashes almost instantly when I start Firefox inside the session. Sometimes FF will start, but VNC will crash very soon after when I start using it.
I don't think I have gotten a VNC session to last more than a couple of minutes. If I just use the terminal in VNC, things seems to be OK.
Edit: VNC also crashes if I start Chromium or Chrome. So I can't browse at all with the browsers currently installed.

The VNC client is unchanged - RealVNC 6.18.907 on Win10. I also tried tightvncviewer on Win10, and I also see the VNC server crash when starting the browser.

The VNC server session is running at 3840x2160x24 bit. This has always been OK on 18.04 on my 10 Gbps LAN.

When this crash happens, I have to
rm /tmp/.X1-lock
rm -rf /tmp/.X11-unix/X1
systemctl restart vncserver@1

But it is fairly pointless, as it just crashes again when I reconnect if I use FF.
 
My settings are as follows :

madbrain@SERVER10G:/etc/systemd/system$ cat vncserver@.service 
[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target

[Service]
Type=forking
User=madbrain
WorkingDirectory=/home/madbrain

PIDFile=/home/madbrain/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 3840x2160 :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target

[EMAIL="madbrain@SERVER10G:~/.vnc"]madbrain@SERVER10G:~/.vnc[/EMAIL]$ cat xstartup
#!/bin/bash
xrdb $HOME/.Xresources
autocutsel -s CLIPBOARD -fork
#unset SESSION_MANAGER
#unset DBUS_SESSION_BUS_ADDRESS
startxfce4 &

Edit: it looks like this has to do with the resolution. If I don't set -geometry or -depth, then I don't see the crashes. I tried doing just -geometry 3840x2160, but I get the same crashes.
-geometry 2560x1600 seems to work, but is not ideal.

Questions :
1) is there some kind of stack trace of the vncserver rcrash ?
2) what is the appropriate place to report this bug ?
3) any workaround/solution ?

---

