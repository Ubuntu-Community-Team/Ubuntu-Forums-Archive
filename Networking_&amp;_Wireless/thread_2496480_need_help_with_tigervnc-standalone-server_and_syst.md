---
title: "need help with tigervnc-standalone-server and system d"
date: 2024-03-30
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2024-03-30
$ lsb_release -a
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 23.10
Release:	23.10
Codename:	mantic

```

$ sudo apt install tigervnc-standalone-server
$ vncserver
```

You will require a password to access your desktops.

Password:
Verify:
Would you like to enter a view-only password (y/n)? n
A view-only password is not used

New Xtigervnc server 'plexmediaserver:1 (lance)' on port 5901 for display :1.
Use xtigervncviewer -SecurityTypes VncAuth -passwd /tmp/tigervnc.YeJlgE/passwd :1 to connect to the VNC server.
$ vncserver -kill :1
Killing Xtigervnc process ID 113593... success!

```

$ sudo vim /etc/systemd/system/vncserver@.service 
```

[Unit]
Description=Remote desktop service (VNC)
After=syslog.target network.target 

[Service]
Type=forking
PIDFile=/home/lance/.vnc/%h%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i
ExecStart=/sbin/runuser -l lance -c "/usr/bin/vncserver %i -geometry 1280x1024"
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target

```
sudo systemctl daemon-reload

Error I get
sudo systemctl start [email]vncserver@1.servic[/email]e
sudo systemctl status [email]vncserver@1.servic[/email]e
```

× vncserver@1.service - Remote desktop service (VNC)                               
     Loaded: loaded (/etc/systemd/system/vncserver@.service; disabled; preset: enabled)   
     Active: failed (Result: exit-code) since Sat 2024-03-30 02:01:15 MDT; 34s ago     Process: 118717 ExecStartPre=/usr/bin/vncserver -kill :1 (code=exited, status=1/FAILURE)
    Process: 118720 ExecStart=/sbin/runuser -l lance -c /usr/bin/vncserver 1 -geometry 1280x1024 (code=exited, status=1/FAILURE)
        CPU: 277ms

Mar 30 02:01:14 plexmediaserver systemd[1]: Starting vncserver@1.service - Remote desktop service (VNC)...
Mar 30 02:01:15 plexmediaserver vncserver[118717]: vncserver: The HOME environment variable must be set.
Mar 30 02:01:15 plexmediaserver systemd[1]: vncserver@1.service: Control process exited, code=exited, status=1/FAILURE                                                
Mar 30 02:01:15 plexmediaserver systemd[1]: vncserver@1.service: Failed with result 'exit-code'.
Mar 30 02:01:15 plexmediaserver systemd[1]: Failed to start vncserver@1.service - Remote desktop service (VNC).

```

---

