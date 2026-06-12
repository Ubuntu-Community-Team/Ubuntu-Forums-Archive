---
title: "I need help - vnc stopped working"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by grahams on 2007-01-17
Hi

I've been using the setup at 

[http://www.ubuntuforums.org/showthread.php?t=122402&highlight=howto+vnc](http://www.ubuntuforums.org/showthread.php?t=122402&highlight=howto+vnc) 

for months on edgy, but recently it just stopped working on 2 different systems and I need help.

This is the output I get from vncviewer

$ vncviewer :1
VNC viewer version 3.3.7 - built Jul 4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password:
ReadFromRFBServer: rdr::EndOfStream
Edit/Delete Message
Looks like Xvnc stopped running.

ps -ef |grep vnc
grahams1 7400 5040 0 09:18 pts/0 00:00:00 grep vnc

If I start Xvnc manually I get "error opening security policy file /etc/X11/xserver/SecurityPolicy"
My systems do not have a directory at /etc/X11/xserver

Is this a bug ? If not how do I fix it?

---

### Post by grumpymole on 2007-01-17
grahams,

vnc4server is currently [ broken in feisty and edgy]("http://grumpymole.blogspot.com/2007/01/vnc4server-on-feisty-breakage.html") with the latest updates.  See [bug #78282]("https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282").

One alternative is to downgrade the package to the earlier version, another is to use x11vnc instead.  This serves the existing desktop on :0 and depends on your requirements.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by grahams on 2007-01-17
Many thanks the reply. 

This bug looks like it's my issue as I have it on 2 systems and there's no common thread apart from a recently apt-get updated them both. 

The 1st line of the bug description says this happened in Jan 06, I guessing the author meant to say 2007 and that makes sense for the timing of my issue.

I'll try your suggested work arounds  and report back .

---

### Post by grahams on 2007-01-17
I can confirm that downgrading vnc4server cures the problem.

Go into synaptic find vnc4server and use force to install the old version. Then lock it to that version to stop it being updated automatically.

---

### Post by notquitehere188 on 2007-04-28
how would i go about doing that?

---

### Post by grumpymole on 2007-04-28
You can also get it working without downgrading.  Add "-extension -XFIXES" to your vnc4server server_args.

Regards

---

### Post by notquitehere188 on 2007-04-28
how?

---

