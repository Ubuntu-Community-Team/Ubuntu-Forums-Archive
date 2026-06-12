---
title: "[SOLVED] hosting local game on LAN"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by bjk on 2008-07-16
Hi, Im trying to host a local game on my home LAN and I'm having a problem with the games server. The game is Wesnoth. 

Here is the result from running wesnothd:

bri@bjk-desktop:~$ wesnothd
could not make fifo at '/var/run/wesnothd/socket'
failed to open fifo at '/var/run/wesnothd/socket'
20080716 22:28:05 error server: Caught network error while server was running. Aborting.: Could not bind to port

any help would be greatly appreciated,

thanks.

---

### Post by bjk on 2008-07-16
I have just discovered that I was starting the server wrongly, the command I needed was:

sudo /etc/init.d/wesnoth-server start

thanks anyway.

---

### Post by markhadman on 2008-12-29
very useful, that!

It really should be at least hinted at in 'man wesnothd', it's really misleading when it says:

SYNOPSIS
       wesnothd [-dv] [-c path] [-p port] [-t number] [-T number]
       wesnothd -V

n'est pas?

---

