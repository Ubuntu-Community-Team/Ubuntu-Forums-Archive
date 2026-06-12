---
title: "Live remote screen view using x11vnc on server - client xtightvncviewer"
date: 2015-08-24
forum: Networking &amp; Wireless
---

### Post by makem2 on 2015-08-24
I have been running x11vnc server on a Raspberry Pi2 for some months now, accessing it from Windows 8.1 using Tightvnc viewer, a gui interface. This just needed the local ip address, username and when connected, the password.

I have installed the xtightvncviewer package on Kubuntu but can see no way to use it via a gui. Is there a gui available, I can't find one?

I have tried several variations of commands from the command line and although I appear to be logged in (password accepted), no live desktop :-(

The user allowed access to the server is pi and I am logged into the client as makem so need to use pi@ip address I believe.

Help?

---

### Post by steeldriver on 2015-08-24
Unless you are tunneling the connection, there is no user-based authentication involved AFAIK: you just type

```

xtightvncviewer [HOST][:DISPLAY]

```

(i.e. the hostname or IP address and - optionally - the port) or
```

xtightvncviewer [HOST][::PORT]

```

and then provide your VNC password at the prompt. You should also be able to replace 'xtightvncviewer' by the simpler generic 'vncviewer' (which is provided via the update-alternatives mechanism).

I'm not aware of a GUI mode for xtightvncviewer specifically, however other VNC clients are available (although some are gnome-based and may introduce additional gnome dependencies, which you may not want on a KDE-based system).

---

### Post by slickymaster on 2015-08-24
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by makem2 on 2015-08-24
> **steeldriver said:**
> Unless you are tunneling the connection, there is no user-based authentication involved AFAIK: you just type

```

xtightvncviewer [HOST][:DISPLAY]

```

(i.e. the hostname or IP address and - optionally - the port) or
```

xtightvncviewer [HOST][::PORT]

```

and then provide your VNC password at the prompt. You should also be able to replace 'xtightvncviewer' by the simpler generic 'vncviewer' (which is provided via the update-alternatives mechanism).

I'm not aware of a GUI mode for xtightvncviewer specifically, however other VNC clients are available (although some are gnome-based and may introduce additional gnome dependencies, which you may not want on a KDE-based system).

```

makem@newTOSH:~$ xtightvncviewer 192.168.2.200:0
xtightvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
makem@newTOSH:~$ xtightvncviewer 192.168.2.200::5500
xtightvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
makem@newTOSH:~$

```

I believe this is due to me, makem, attempting to log in when not a registered user.

Trying registered user pi:

```

makem@newTOSH:~$ xtightvncviewer pi@192.168.2.200:0
Couldn't convert 'pi@192.168.2.200' to host address
makem@newTOSH:~$ xtightvncviewer pi@192.168.2.200::5500
Couldn't convert 'pi@192.168.2.200' to host address
makem@newTOSH:~$ 

```

---

### Post by steeldriver on 2015-08-24
Have you confirmed that a VNC server is running and listening on the expected port, and is not closed by a firewall? e.g.

```

sudo netstat -nlpt | grep -i [v]nc

```

(run on the pi)?

---

### Post by makem2 on 2015-08-24
Just done that and yes, it was running but corrupted by all the  different attempt I had been making to connect. I could not connect from  a windows client.

Rebooted and now working correctly as pointed out:

```

makem@newTOSH:~$ xtightvncviewer 192.168.2.200
Connected to RFB server, using protocol version 3.8
Enabling TightVNC protocol extensions
Performing standard VNC authentication
Password: 
Authentication successful
Desktop name "xxx:0"
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0

```

I see from that that although I have been using pi to connect from windows I can connect as user makem. therefore connections are password specific, not user. I was sure I set x11vnc with a username but maybe not.

Thanks for the help, sorry it took a while to get to reboot.

---

