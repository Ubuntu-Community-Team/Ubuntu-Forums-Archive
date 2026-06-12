---
title: "auto-login ubuntu server?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by dphirschler on 2009-01-29
Is it possible to set up Ubuntu server to auto-login?  This is for my home file server (Ubuntu Server 8.10) and I want it to come back up in case of a power outage.


Darryl

---

### Post by khedron on 2009-01-29
This should be settable in the BIOS. You typically get into the BIOS menu by pressing a key straight after power on (F5 or something depending on what BIOS it is).

On my Dell, the relevant setting is something like "When power is restored, [turn on] [stay off] [go into state we were before power loss]" (obviously I am hugely paraphrasing).

*Edit: Since this is a file server I assume you didn't really mean auto-login, but auto-startup*

---

### Post by dphirschler on 2009-01-29
Well, what I meant was for it to auto-login... but now that I think about it, I don't have to be logged in for the file server to work.


Darryl

---

### Post by lazyart on 2009-01-29
Yeah, and auto login for a server would be a huge security no-no.

---

### Post by BDNiner on 2009-01-29
You will have access to all the services that your server provides without loggin it in. unless you sit infront of the server to actually do work.

---

### Post by Insightfill on 2009-01-29
> **BDNiner said:**
> You will have access to all the services that your server provides without loggin it in. unless you sit infront of the server to actually do work.
In which case, you can also probably just hit the power button, too!  :p

The one situation where I've found the autologin useful is a machine for which you also need remote VNC access.  Since the Vino server doesn't kick in until you're logged in, you're kinda stuck.

In that case, it also pays to have a locking screen saver set up with a small timeout window.  if you restrict VNC to only allow local connections, then it effectively closes off the VNC as an attack vector.  Of course, the console itself is still active.  Security is never perfect, is it?

---

### Post by dphirschler on 2009-01-30
It's a headless server stuck over in the corner.  I just lost my head temporarily about auto-login.  I completely forgot that it is still working even if nobody is logged in.  But VNC might become important when/if I install Gnome.  But even then, I can login through PuTTY and then run VNC as I've done in the past.


Darryl

---

### Post by khedron on 2009-01-30
If you just want to run a few programs off the server, you can use Putty's built-in X11 forwarding instead of bothering with VNC - just install Cygwin and its X11 packages and start an X server locally, then run the program over ssh.

I'm not trying to say that this is a better way, just giving options.

---

