---
title: "Xvnc and multi-sessions"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by kamkos on 2008-08-22
Hey,

I am trying to run Xvnc in multi-user environment. Everything is working fine except i cannot make more than 2 connections to Xvnc at the same time. 

my Xvnc file started with xinetd:

```
service vnc2
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5903
}
service vnc1
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5902
}
service vnc3
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :3 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5904
}

I have also added the following lines to /etc/services

vnc1    5902/tcp
vnc2    5903/tcp
vnc3    5904/tcp
```


The deal is that I can make two connections to the server but not three at the same time. For example, if vnc1 and vnc2 is on then vnc3 cannot be made with the given error: 

read: Connection reset by peer (10054)

Any help will be appreciated.

kamkos

---

### Post by jpeddicord on 2008-08-22
Not a tutorial, moved to Networking.

---

### Post by kamkos on 2008-08-23
anybody?

---

### Post by spooner on 2009-01-16
This is a GDM problem...

Somewhere in the gdmconfig file there is a line limiting the number of connections to the GDM from any one host. Using the above method you are connecting to the GDM from a vnc service running on localhost so although you are not at localhost GDM still thinks you are. Just increase the number of connections to a few more that you will ever need.

Hope this helps.

---

### Post by spooner on 2009-01-16
Also thought I should add that you should find the line in 

/etc/gdm/gdm.conf

and then copy and paste it to the correct section of 

/etc/gdm/gdm.conf-custom

& then edit it to your needs. I could find the line for you but I'm in a lazy mood.

---

