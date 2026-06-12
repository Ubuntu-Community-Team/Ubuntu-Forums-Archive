---
title: "RFB protocol version 4.0 needed"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by DJ_Peng on 2007-04-19
An internet radio station that I've been working with since my WinXP days uses the Enterprise version of RealVNC for remote access purposes. Unfortunately since I switched to Ubuntu I have been unable to connect to their computer to do some tech work I'm supposed to be doing. I've tried the Terminal Server Client, the vncviewer, vnc4viewer, and xtightvncviewer. Nothing works. This is what I get when I try with vnc4viewer> VNC Viewer Free Edition 4.1.1 for X - built Jan  7 2007 17:30:38
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Thu Apr 19 19:42:52 2007
 CConn:       connected to host ##.##.##.## port 5900

Thu Apr 19 19:42:53 2007
 CConnection: Server supports RFB protocol version 4.0
 CConnection: Using RFB protocol version 3.8
 CConnection: No matching security types
 main:        No matching security typesI've searched not only these forums but also the 'net in general but I can't find a way to upgrade my RFB proticol. Is there something I'm missing?

They do have the Enterprise version of VNC, but for Windows so that really doesn't do me any good for the viewer unless I install it under Wine, which I'm really trying to avoid if there's a Linux native solution.

---

### Post by DJ_Peng on 2007-04-21
I downloaded the VNC Enterprise Edition for Unix from the RealVNC site ,  installed it, and am able to use the viewer to connect to the station's computer. We can mark the thread resolved.

---

### Post by lindylex on 2008-04-17
DJ_Peng, your solution worked like a charm.  I was trying to log into a vnc sever and received this error.

VNC viewer version 3.3.7 - built Dec 30 2006 12:48:54
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 4.0 (viewer 3.3)
VNC connection failed: No configured security type is supported by 3.3 viewer

The server is an enterprise version of RealVNC protocol 4.0.

I used vncviewer from terminal and it looked like it did not support that version protocol so I installed the VNC Enterprise Edition.  Tthe viewers are free for each platform.

Go to this link then click on "Proceed To Download"
[http://www.realvnc.com/cgi-bin/download.cgi](http://www.realvnc.com/cgi-bin/download.cgi)

To get the correct version for any platform, Mac, Windows, Linux, Solaris, any Nix etc.

Thanks, Lindylex

---

