---
title: "Not able to get a working xrdp session"
date: 2020-11-17
forum: Networking &amp; Wireless
---

### Post by franknfurter2 on 2020-11-17
Hello out there,

my use case is to get an rdp session to an Ubuntu 18.04.5 LTS System. So I installed xrdp and output of "systemctl status xrdp" shows
```
 xrdp.service - xrdp daemon
   Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2020-11-17 20:29:32 CET; 26min ago
     Docs: man:xrdp(8)
           man:xrdp.ini(5)
  Process: 25230 ExecStop=/usr/sbin/xrdp $XRDP_OPTIONS --kill (code=exited, status=0/SUCCESS)
  Process: 25243 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=0/SUCCESS)
  Process: 25235 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)
 Main PID: 25244 (xrdp)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/xrdp.service
           &#9492;&#9472;25244 /usr/sbin/xrdp

Nov 17 20:29:31 <hostname obfuscated> systemd[1]: Starting xrdp daemon...
Nov 17 20:29:31 <hostname obfuscated> xrdp[25243]: (25243)(140257481279296)[DEBUG] Testing if xrdp can listen on 0.0.0.0 port 3389.
Nov 17 20:29:31 <hostname obfuscated> xrdp[25243]: (25243)(140257481279296)[DEBUG] Closed socket 7 (AF_INET6 :: port 3389)
Nov 17 20:29:31 <hostname obfuscated> systemd[1]: xrdp.service: Can't open PID file /var/run/xrdp/xrdp.pid (yet?) after start: No such file or directory
Nov 17 20:29:32 <hostname obfuscated> systemd[1]: Started xrdp daemon.
Nov 17 20:29:33 <hostname obfuscated> xrdp[25244]: (25244)(140257481279296)[INFO ] starting xrdp with pid 25244
Nov 17 20:29:33 <hostname obfuscated> xrdp[25244]: (25244)(140257481279296)[INFO ] listening to port 3389 on 0.0.0.0
```

I tried to connect with ufw enabled and disabled. Started tcpdump to see if request reaches the host (it did) and analyzed the log files. journalctl -xe founds an entry like

```
polkitd(authority=local)[1333]: Unregistered Authentication Agent for unix-process:25650:34595746 (system bus name :1.9361, object path /org/freedesktop/PolicyKit1/AuthenticationAgent
```

after restarting the service.

vnc is not an option.

Has somebody an idea how to analyze this failure. By the way: does a vnc server have to be installed as well to get it work? Some postings tell this.

Regards

Frank

---

### Post by HermanAB on 2020-11-18
It is a server.  For X applications, you need to run an X server, but a server usually doesn't have one.

The Ubuntu server version offers you SSH access by default.  You can do anything with SSH.  Read the snailbook at snailbook.com (You can read it online for free).

Even Windows10 now comes with SSH, so there is little excuse not to use SSH.

VNC is an ancient Windows idea which is usually not a good idea on a UNIX system.  Your local host presumably already has a perfectly good desktop.  Overwriting your nice and fast local desktop with a slow remote desktop is a waste of time, if you only want to run remote application programs.  Basically, a 'desktop' is just a maximized file browser and running it is useless, if you are going to overwrite the screen with an application.  SSH can run a remote server program transparently on your local desktop.

If you really, really, really want GUI programs on your server despite all the security warnings by all the security gurus, install the XFCE desktop.  It works with Xorg (That is the X in XFCE) and provides a bunch of GUI programs, which you can then launch with SSH, to display on your local host.

However, note that with SSH, you do not need to actually run XFCE and Xorg to run GUI programs remotely! You just need to have it installed, in order to get the GUI programs to install.  Once installed, you can run any GUI program on the server remotely over SSH, provided that your local machine is running an X server.  This works because the sshd server on the server, includes an X client that works with the X server on your local host. * If you are still not confused, then you don't need to read the snailbook...*

---

### Post by franknfurter2 on 2020-11-18
Dear HermanAB, thanks for your reply and your advice about sense and non sense of remote GUIs. But the reason for me to post my question was the hope to get some technical advice. So I am still searching for a technical advice about how to analyze xrdp service and why it is not working as expected.

---

### Post by HermanAB on 2020-11-18
Ubuntu normally use Gnome and Gnome normally use Wayland.

Xrdp needs Xorg.

If you would install Xubuntu, then Xrdp should work.

---

### Post by franknfurter2 on 2020-11-19
Dear HermanAB,

thanks a lot. I think, this is the "solution". Such a shame, that synaptic (apt-get) let me install xrdp just singular and does not lead me to the dependency to an x server. I have thought that dependency tracking is one of the main goals of package managers.

New installation of Xubuntu is not an option at the moment. Do you know a rdp or vnc solution for wayland. I gues tightvncserver will not work without an xserver either. Is that right?

---

### Post by HermanAB on 2020-11-19
You *can* install Xorg and configure Gnome to use it instead of Wayland.  A little searching will turn up guides for Ubuntu.  

However, this is error prone, so that is why I have not suggested it.  Backup your data before you attempt this, since you can end up with a black screen, poking around in the dark.  Fortunately when you get a black screen, others cannot see the very nice words that you are typing...

AFAIK, the only way to remote a desktop is with Xorg.  The makers of Wayland consider the remote features of X to be a security hole and a feature which they do not need.  The rest of the world begs to differ though.

---

### Post by slickymaster on 2020-11-19
*Thread moved to **Networking & Wireless**.*

---

### Post by franknfurter2 on 2020-11-20
Ok and thanks for your advices. I will not go from wayland to xorg, because it is worth nothing for my use case. Only using a command line while loggin in using ssh is still not an option, because I need to use a GUI application that is only maintained on the Linux machine. So my question that started this thread is answered (xrdp does not work with wayland) I mark this as solved. But still my use case is not solved.

---

