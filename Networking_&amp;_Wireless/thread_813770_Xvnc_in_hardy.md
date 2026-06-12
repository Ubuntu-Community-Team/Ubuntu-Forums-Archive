---
title: "Xvnc in hardy"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by Jive Turkey on 2008-05-31
I have tried several of the HOWTO posts for getting vnc4server to work after trying also in vain to get vino server working and the errors I get are:

1) "authentication faliure" after entering a password

or 

2) "connection reset by peer (104)"

Does any flavor of vnc work for anyone in Hardy I wonder?

More Details:
```
~$ vncviewer 127.0.0.1:0

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sat May 31 04:59:12 2008
 CConn:       connected to host 127.0.0.1 port 5900
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
<prompts for password, i enter it and voila>
Sat May 31 05:00:18 2008
 main:        Unknown security result from server

```

```
~$ vncviewer localhost:1

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Sat May 31 04:51:14 2008
 CConn:       connected to host localhost port 5901

Sat May 31 04:51:49 2008
 main:        read: Connection reset by peer (104)

```

---

### Post by Jive Turkey on 2008-06-11
anybody?

---

### Post by dbutcher on 2008-06-14
me too!
Can anybody help?

---

### Post by ians1 on 2008-06-14
I tried running VNC on Ubuntu, got the 

desktop is <machine name>:1 message

I then go to the Windows machine running VNC Viewer and type in the name as above for server

I then get VNC Viewer error

```
unable to resolve host by name: The requested name is valid, but no data of the requested type was found. (11004)
```

I can't understand why it does not connect, is it because of Firewalls on the Windows machine?

Any hints would be apprecitated.

thanks

ian

---

### Post by ians1 on 2008-06-14
I might add the object is to be able to control all the computers I use from  one laptop with Windows.

ian

---

