---
title: "Graphic Remote Access using XDMCP and so on"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by mcapelati on 2007-06-27
Hi There!

I'm trying to learn about graphic remote access.

a) I've a machine (wich will be server) running Ubuntu 7.04, IP 192.168.0.88

b) There is another very-old machine (Pentium-100) running old Slack (kernel 2.4.20) for testing purposes.

c) There is another not-so-old machine (Athlon-800) running WinXP.

d) There is an old notebook (Penitum-233 MMX) witch runs Win98, but I'm planning to use Xubuntu on it.

What I want to do is simple: access Ubuntu 7.04 on server (a) using all those old machines, in a graphic way, I mean, use them as I was using the very server (a). 

Sounds quite simple hun ? 

So I started to look all documentation about it, and found things like: RDP, VNC, RDesktop, NX, FreeNX, TightVNC, XDMCP, LTSP, and on, and on, and on....

Seems to me that XDMCP was the first and simple thing (besides "unsecure"?), so I started from the beggining (at least, what I thing was!)

1) On server, I went to System > Administration ... Session Init...and try to enable that.
I note that this makes some little changes on /etc/gdm/gdm.conf-custom file. Even, this file is quite different from "factory-gdm.conf", that has lots of information on it! Seems that 
gdm.conf-custom file misses lots of information... 

2) I went to machine (b), and on prompt, I type: 
X -query 192.168.0.88
Seems that started to work, but only thing I see is that grey screen with an X on midle

3) On machine (c) I installed that CygWin. On terminal Window, I type
run XWin :1 -query 192.168.0.88
Same thing happens:  that grey screen with an X on midle

I started to think that something is going wrong with that /etc/gdm/gdm.conf-custom file, but I really don know from where start to change things manually, and if this is really the right file to change...:(

Please, help me ! How to make this XDMCP works?

Thanks in advance.

---

### Post by Rui Pais on 2007-06-27
hi,
a simple way is:
On the the old machines:
```
gksudo gedit /etc/X11/gdm/gdm.conf
```

search for lines:
> 0=Standard
#1=Standard

change to: 
```
0=Terminal -query 192.168.0.88
#1=Standard
```
or if you want to have a gdm for old and another for 192.168.0.88:
```
0=Standard
1=Terminal -query 192.168.0.88

```

Nothing is need on server side :)


edit:
If you have a gdm.conf-custom on old machine (it depends on how old gdm version is) 
you should make changes on that file, not on gdm.conf, to avoid been overwritten by updates.
just add: 
> [servers]
before the lines

---

