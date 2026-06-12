---
title: "Remote ssh vnc Mac OSX to ubuntu"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by craigni on 2008-11-18
Hi gurus,

I've installed 8.10 Intrepid Ibex and am lovin' it.  In fact, I am lovin' it so much that I'd like to remote login from my Mac OS X laptop to the Ubuntu machine.  Preferably, I'd like to do this with just the Ubuntu machine turned on and no one yet logged into an X session, but if that is too painful, I can just log into an X session on the Ubuntu machine to get things started.  I'd also like to use ssh tunneling for the X session.  (I already can ssh into the Ubuntu machine from the Mac OS X laptop, but am interacting in the usual primitive terminal window.)

What I've done so far:

Installed Chicken of the VNC on the Mac laptop.

Put the following line in ~/.bashrc on the Mac laptop:

```

alias rvnc='ssh -L5900:127.0.0.1:5900 -C craign@192.168.1.XXX'

```

where XXX is the Ubuntu machine's ID on the local router.

Installed x11vnc on the Ubuntu machine:

```

sudo apt-get install x11vnc

```

Now I'm kind of stuck.  I issue rvnc in an xterm window on the Mac laptop, which logs me into the Ubuntu machine.  I then type

```

x11vnc -rfbport 5900 -display :0 -forever &

```

in the xterm window, and it spits out a warning and some other info indecipherable to my feeble brain, and sits there.

Any ideas how to complete this process? :confused:

Many TIA,
Craig

---

### Post by krunge on 2008-11-18
> **craigni said:**
> 

```

alias rvnc='ssh -L5900:127.0.0.1:5900 -C craign@192.168.1.XXX'

```

where XXX is the Ubuntu machine's ID on the local router.

Now I'm kind of stuck.  I issue rvnc in an xterm window on the Mac laptop, which logs me into the Ubuntu machine.  I then type

```

x11vnc -rfbport 5900 -display :0 -forever &

```

in the xterm window, and it spits out a warning and some other info indecipherable to my feeble brain, and sits there.

Your description sounds like a good plan.

Did you try to connect with the vncviewer yet?  If x11vnc didn't exit, it is probably ready for you to connect to it.

[http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)

I assume user 'craign' is already logged into an X session on ubuntu, right?

If not (e.g. GDM login greeter is running), consider:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

---

