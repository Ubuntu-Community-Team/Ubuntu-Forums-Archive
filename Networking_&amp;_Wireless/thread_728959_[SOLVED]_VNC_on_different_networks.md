---
title: "[SOLVED] VNC on different networks"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by ScottKinkade on 2008-03-19
Hi, I have ubuntu gutsy on my desktop and on my laptop. I would like to connect (using the remote desktop program that comes on gutsy) from my laptop on a different network to my desktop on my home network. Is this possible? If so, how? Thanks.

---

### Post by stalker145 on 2008-03-19
> **ScottKinkade said:**
> Hi, I have ubuntu gutsy on my desktop and on my laptop. I would like to connect (using the remote desktop program that comes on gutsy) from my laptop on a different network to my desktop on my home network. Is this possible? If so, how? Thanks.

Totally possible.

The easiest way to go about this is to set up Remote Desktop on the computer you wish to access (System ~> Preferences ~> Remote Desktop) and forward port 5900 through your router to this computer. After that, either memorize your IP (a pain since it may change) or set up a dynamic DNS service (e.g. DynDNS or NoIP) to point to your router. Many routers nowadays have the option of updating these services when the router's IP address changes.

Make sure if you use port 5900 (which is the default) that you set up a **VERY** strong password as VNC is inherently insecure (unsecure? not secure? however it's said).

You're done. You can now access your remote computer via VNC by dropping to the terminal and typing one of the following:```
vncviewer xxx.xxx.xxx.xxx

or

vncviewer yourdomain.tld
```

Personally, I use NoMachine. It's very easy to set up (simple .deb file installations) and it is much more secure since it uses SSH vice open communications as VNC does.

Check back if you need more help with this.

---

### Post by ScottKinkade on 2008-03-19
ok, that is GREAT!!! But one problem (and i may sound like a total noob); how do i forward a port? :-/ all the other computers on my network are running windows. How do i do this so my connection is the most secure connection possible? Thank you SO much!!!

---

### Post by wormser on 2008-03-20
> **ScottKinkade said:**
> ok, that is GREAT!!! But one problem (and i may sound like a total noob); how do i forward a port? :-/ all the other computers on my network are running windows. How do i do this so my connection is the most secure connection possible? Thank you SO much!!!

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

To make it secure you need to tunnel VNC through ssh.  You will need to forward port 22.  There should be a guide here on the forum.  Here is a quick rundown.  Make sure you have the firewall, the ssh server and the rest set up.

```
ssh -C -L 5900:localhost:5900 username@ipaddress.com
```

The -C is for compression and -L is to bind the local port 5900 to the remote port 5900.

```
xvncviewer localhost:5900
```

---

