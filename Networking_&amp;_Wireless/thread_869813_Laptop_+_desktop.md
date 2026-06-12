---
title: "Laptop + desktop"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Venality on 2008-07-25
Is there any way i can control my desktop with my laptop so i can use my monitor, mouse, and keyboard with my laptop..

I want to do this because I'm running out of space on my laptop, and i dont have the money to buy a new HDD. so is there any solution to my problem.

my laptop is new and performs better then my desktop so i use it for gaming, but all my media needs are on Ubuntu partition. and my desktop is full ubuntu.

---

### Post by Yannick Le Saint kyncani on 2008-07-25
Hi Venality,

Well if you're running out of disk space, it looks to me like you just have to share some disk space from your desktop to your laptop.

So you may want to setup sshfs, or samba, or nfs, ...
There are some very good howto for those on the internet.

---

### Post by superprash2003 on 2008-07-25
which OS is the desktop running?

---

### Post by Venality on 2008-07-25
er... it says in the first post its full ubuntu

---

### Post by superprash2003 on 2008-07-25
enable remote desktop in your desktop under system->preferences->remote desktop.. then on your laptop go to the terminal and type vncviewer x.x.x.x:0 where x.x.x.x is the ip of the desktop

---

### Post by Venality on 2008-07-25
i get this error

VNC server supports protocol version 3.7 (viewer 3.3)
VNC connection failed: No security type suitable for RFB 3.3 supported

---

### Post by aminalid on 2008-10-09
> **Venality said:**
> i get this error

VNC server supports protocol version 3.7 (viewer 3.3)
VNC connection failed: No security type suitable for RFB 3.3 supported

Same problem here.

i tried installing realvnc and it gave me a slightly more detailed error:
```

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Thu Oct  9 10:21:12 2008
 CConn:       connected to host 192.168.0.1 port 5900
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
 CConnection: No matching security types
 main:        No matching security types


```
I googled a lot but no results yet. Did you solve this?

---

### Post by aminalid on 2008-10-10
I found this useful vncviewer option:
```

vncviewer -log=CConnection:stderr:100 192.168.0.1

```
this outputs
```

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Fri Oct 10 16:05:37 2008
 CConnection: reading protocol version
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
 CConnection: processing security types message
 CConnection: Server offers security type [unknown secType]( 18 )
 CConnection: No matching security types

```

So the unknown security type is 18.
Using [this document]("http://www.realvnc.com/docs/rfbproto.pdf") (page 9-10) i found that the unknown type the server is offering is TLS.
Which is:
> TLS, standing for Transport Layer Security, is the latest version of SSL. It is an enhancement of SSL version 3.0, and is a proposed Internet Standard (see RFC2246) 

I checked that i have the latest version of openSSL installed, and now i am stuck again. 
Do i have to configure SSL somehow to make it work? Any ideas?

---

### Post by ufhero on 2008-11-19
> **Venality said:**
> i get this error

VNC server supports protocol version 3.7 (viewer 3.3)
VNC connection failed: No security type suitable for RFB 3.3 supported

I had this same problem when VNCing into an ubuntu server running the GNOME desktop. 

I solved the problem by disabling the "Require Encryption" in the "Security" section of the "Remote Desktop Preferences" "Advanced" tab. 

To get there click: System > Preferences > Remote Desktop

---

### Post by roryc420 on 2009-02-10
> **ufhero said:**
> I had this same problem when VNCing into an ubuntu server running the GNOME desktop. 

I solved the problem by disabling the "Require Encryption" in the "Security" section of the "Remote Desktop Preferences" "Advanced" tab. 

To get there click: System > Preferences > Remote Desktop

Can anyone please tell me if this is possible from an ssh session? I'm not currently at home so i have no way of making the settings adjustment any other way.

---

### Post by ufhero on 2009-03-10
You may want to also try the method explained by Juilet Kemp, "Remote Desktop With GDM". It will also work with KDM. It uses Xnest. You will find the tutorial here: [http://www.serverwatch.com/tutorials/article.php/3809291](http://www.serverwatch.com/tutorials/article.php/3809291)

Note: This is not VNCing. It allows you to get a remote login from your desktop manager e.g. (GDM,KDM).

For more information on Xnest and another method point your browser to: [http://en.wikipedia.org/wiki/Xnest](http://en.wikipedia.org/wiki/Xnest)

And check out the man page for xnest.

---

