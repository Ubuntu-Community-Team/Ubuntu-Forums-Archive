---
title: "No remote desktop on Jaunty"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Curbuntu on 2009-05-11
[SIZE=3]I've seen variations on this problem, but not quite the same as mine.  Remote Desktop worked fine on my two machines under Ubuntu 8.10 (and earlier versions).  But I can't get it to work on Jaunty.  My laptop (a 5-year-old Compaq Presario) dual-boots 8.10 32-bit (where RD works)...

[/SIZE][ATTACH]113420[/ATTACH][SIZE=3] 
[/SIZE][ATTACH]113418[/ATTACH]

...[SIZE=3]and 9.04 64-bit (where RD *doesn't *work).
[/SIZE][ATTACH]113419[/ATTACH][SIZE=3]  

I also upgraded a older, slower desktop from U8.10 to Xubuntu 9.04 (both 32-bit).  Same situation there -- it worked in 8.10 but not 9.04.

It doesn't matter if I access the machines from a Windows box running Real VNC or from an Ubuntu box running RD Viewer; the messages I get (respectively) are:

1) Failed to connect to server! or
2) Connection closed; Connection to host x.x.x.x:5900 was closed.

These 9.04 machines can't even remotely connect to themselves as localhost or 127.0.0.1.  However, they can both access the Internet just fine, they can print, and they can ping and be pinged.

FWIW, I don't need to VNC to these from outside my router/firewall; I only need to connect from within the confines of my own local network.

I'm sure I'm missing something, but after several days, I haven't figured out what it is.  Any help is appreciated.  Thanks in advance!
[/SIZE]

---

### Post by ptn107 on 2009-05-12
I just enabled remote desktop in 9.04 to test it out and used vinagre (Applications -> Internet -> Remote Desktop Viewer) to connect.  Connecting from another 9.04 Ubuntu machine on the local net works, as well as the machine connecting to itself (localhost).  The only thing I can think of is maybe the 9.04 machine of yours has a local firewall configured (firestarter, [g]ufw?; check iptables).

---

### Post by Curbuntu on 2009-05-12
[SIZE=3]I'm not certain how to accurately respond to your points, but I'll try:

1) **sudo ufw status** reports: "Status: inactive"
2) Add/Remove reports that Firestarter isn't installed.
3) I'm not certain how to check the iptables.
[/SIZE]

---

### Post by Curbuntu on 2009-05-17
[SIZE=3]Here's an additional question since no resolution has been reached on this yet -- why is there no "Advanced Tab" in RD server setup?  It's almost as though the old "Only Allow Local Connections" setting were checked (under "Network"); but now, without the tab, there's no way to access or access this.[/SIZE]

---

### Post by XCan on 2009-05-17
> **Curbuntu said:**
> [SIZE=3]Here's an additional question since no resolution has been reached on this yet -- why is there no "Advanced Tab" in RD server setup?  It's almost as though the old "Only Allow Local Connections" setting were checked (under "Network"); but now, without the tab, there's no way to access or access this.[/SIZE]

That is a **very** good question, and I've no idea why they felt this was a bright idea. However, I found out that you can access some of the advanced options by running
```
gconf-editor
```
and browsing to desktop -> gnome -> remote_access, which is particularly useful if you want to run the server on an alternate port.

---

### Post by Curbuntu on 2009-05-17
XCan,
I couldn't find anything in the gconf-editor settings that will help, but having you point out to me the existence of gconf-editor is very helpful for future projects.  Thank you!

I wonder -- does this problem only happen in the 64-bit version of ubuntu 9.04?

---

### Post by BDNiner on 2009-05-17
I enabled remote desktop on my computer and it works fine. I am able to connect and the computer is listed in the "hosts nearby" section of Remote Desktop Viewer application.

---

### Post by Efros on 2009-05-17
You could try disabling the resident RD application and install x11vnc. I've done this on a couple of machines due to the resident app not refreshing the screen when using compiz.

---

### Post by sparklyprgs on 2009-07-05
> **XCan said:**
> That is a **very** good question, and I've no idea why they felt this was a bright idea. However, I found out that you can access some of the advanced options by running
```
gconf-editor
```
and browsing to desktop -> gnome -> remote_access, which is particularly useful if you want to run the server on an alternate port.

Thanks XCan!! I spent quite a while trying to find the missing "lock screen on disconnect" option (it used to be on the Advanced tab in 8.10). It's in the exact same section.

---

