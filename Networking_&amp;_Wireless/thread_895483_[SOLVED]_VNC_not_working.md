---
title: "[SOLVED] VNC not working"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Jamina1 on 2008-08-20
Hi guys.

I recently turned an old windows machine into a LAMP box using Ubuntu Server 8.04.

Both computers are on the same local LAN and I can access the webpage on the server just fine from my main computer. 

Problem is I don't have a monitor to dedicate to this server all the time so I was hoping to get VNC up and running so I could remotely connect to it. So I installed ubuntu-desktop on my server so I'd have an X environment.

Problem is, I've installed tightvncserver (apt-get install tightvncserver) and I've installed the viewer on my Windows XP box and I cannot connect to the Linux box.

I've tried via hostname, IP address, nothing. I even tried installing RealVNC viewer to see if it was maybe a glitch with the software, but no go.

What am I doing wrong?

---

### Post by jtniehof on 2008-08-20
> **Jamina1 said:**
> Problem is, I've installed tightvncserver (apt-get install tightvncserver) and I've installed the viewer on my Windows XP box and I cannot connect to the Linux box.
Did you actually start the server on the linux box, or just install it?

---

### Post by Jamina1 on 2008-08-20
> **jtniehof said:**
> Did you actually start the server on the linux box, or just install it?

If you mean typing the command "vncserver" then yes, I did that, and even then no joy.

---

### Post by jtniehof on 2008-08-21
Try:
```
netstat -t -u -a | grep LISTEN
```
on the linux box after starting the VNC server. There should be a line that looks like:
```
tcp  0  0 *:5901  *:*  LISTEN
```
If there isn't, then post the entire output.

Also, could you be more specific on "cannot connect"? What are you doing and what is the result?

---

### Post by Jamina1 on 2008-08-21
I figured out what was wrong. I had to specify a "screen" to connect to. 

Once I did that, I connected.

It took me a little bit to figure out how to get programs to show up on that screen though, but I figured it out!

Hooray, server box with limited GUI capabilities!

---

