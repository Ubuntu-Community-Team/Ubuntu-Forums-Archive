---
title: "remote desktop suddenly broke"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by formol on 2008-11-08
Hello,

I'm using remote desktop between two computer in my flat, both are on 8.04.

First i got it work with 
>  Originally Posted by dvfreelancer
I made a breakthrough and got it working. It's a strange work-around and you have to do it exactly this way or it doesn't work.

Go to System > Preferences > Remote Desktop

Uncheck the Require User To Enter This Password box.

Check the box again, enter the password and hit RETURN before closing the dialog box. 

It worked.  and I was using the computer remotely, suddenly the remote desktop connection broke.
when I try to reconnect, it said :

> formol@MainBuntu:~$ vncviewer 192.168.0.199:0

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Sat Nov  8 01:29:37 2008
 main:        unable to connect to host: Connection refused (111)


I google it, and nothing, someone got an idea?

thank you

---

