---
title: "x11vnc killed after login"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by erwall on 2006-12-19
on 6.10...

trying to setup x11vnc server at boot time.

in /etc/X11/gdm/Init/Default:

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5901

I connect and I get the logon screen, enter username and password and login and it drops the connection and kills the x11vnc process.

x11vnc.log:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (MIT-SHM)
  Minor opcode of failed request:  4 (X_ShmGetImage)
  Serial number of failed request:  4355
  Current serial number in output stream:  4357

From everything I've found it's like KillInitClients=true in gdm.conf but it's not, it's KillInitClients=false

I can issue the command line to start x11vnc once logged in and I can connect/reconnect just fine.

Any ideas?

---

### Post by krunge on 2006-12-22
That is a strange one.  Does it happen to work if you add -noshm to the cmdline?

But as you say you can start it manually after your session is started, so not
clear why shm would start working properly after you log in...

Looking at the xorg shm.c file, the only thing I can think of is that the shm drawable
isn't realized yet, maybe try  (sleep 10; x11vnc ....) & in the gdm script?

There is a check in shm.c WRT being outside some border width, but I can't
see how that would apply to the root window (i.e. the full display).

---

### Post by krunge on 2006-12-22
Re-reading your post:

> I connect and I get the logon screen, enter username and password and login and it drops the connection and kills the x11vnc process.

I think now that it is just a KillInitClients issue.  Have you restarted gdm since modifying
gdm.conf?  Are you sure your changes to gdm.conf are being picked up and are correct?
Maybe change some other parameter in the file and see if it is picked up after restarting
gdm (restarting might be like: /etc/init.d/gdm restart)

---

### Post by fromage4000 on 2007-04-13
I have almost the exact same problem.  KillInitClients=false but x11vnc seems to die anyway.  x11 vnc restarts find from command line.  The weirdest thing of all to me is that it used to work fine, when I used my motherboard's onboard video and the corresponding xorg.conf.  I recently added a new video card and had to change my xorg.conf file.  Ever since that change x11vnc works at login and then dies without anything else having changed.  I haven't tried removing the card and reverting to the old xorg.conf yet but I can't imagine why xorg.conf should even matter to x11vnc or why having a new xorg.conf would cause the gdm.conf to stop allowing init clients.

---

