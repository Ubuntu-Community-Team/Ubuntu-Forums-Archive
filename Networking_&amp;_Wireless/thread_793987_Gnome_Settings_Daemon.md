---
title: "Gnome Settings Daemon"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Gotou on 2008-05-14
Hullo!

A gremlin has made it's home in my computer and I'd like to evict the critter.

Just installed Heron and downloaded all the programs I wanted and when I reboot this showed up when Gnome loads:


"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background
settings may not work correctly.

The last error message was:

Did not receive a reply.  Possible causes include: the remote
application did not send a reply, the message bus security
policy blocked the reply, the reply timeout expired, or the
network connection was broken.

GNOME will still try to restart the setting Daemon next time
you log in."


Since I dumped everything in at once through Synaptic I don't have a clue as to which downloaded proggy is the culprit.

What I have been able to figure out is that this message only pops up when I have my router turned off (computer -> firewall router -> modem).  If the router is on, my computer happily boots with no qualms.

So what I figure is something in Gnome is trying to either connect to my network or connect to a server out on the Internet.

Any ideas what log file(s) would indicate what is going wrong?

Better yet, a solution to this puzzle.

Thanks.

---

### Post by GXX on 2008-05-14
Did you try logging out and logging back in? I did that and it restarted just fine.

---

### Post by Gotou on 2008-05-14
Yup.

Logged off, logged back in.

Restarted.

Shutdown everything, waited serveral seconds and turned back on.

Router on (connected to network) = happy computer.

Router off (dis-connected from network) = constipated computer.

:confused:

---

### Post by NIT006.5 on 2008-05-25
The router on/off making a difference has got me a bit confused, but I have just discovered that I was getting this error because my loopback interface wasn't working.The settings daemon obviously relies on a "network connection", which is the loopback by default I'm sure. Perhaps in your case, the connection is coming back to your PC via the router? That's the only remotely logical explanation I can think of to explain why it works when you're connected to the network. 

Try:
```

ping 127.0.0.1

```

If you get a reply, then it's a different problem (could be that "localhost" is resolving to your external network address and not the loopback?). If you don't get a reply, then check your /etc/network/interfaces file and make sure the loopback interface is defined. It should look something like:

```

auto lo
iface lo inet loopback

```

If that doesn't appear, try adding it in. Then restart network:

```

sudo ifdown -a --force
sudo ifup -a --force

```

Then see if your loopback ping works now. If working, then logout and test logging in again. Good luck and hope that helps :)

---

