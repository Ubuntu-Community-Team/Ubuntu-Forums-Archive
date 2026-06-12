---
title: "Vnc hangs my laptop randomly"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by VeganZombie on 2007-03-08
I'm having an issue with while trying to access my Ubuntu box from my Windows machine. When I VNC in, everything runs fine, but every once in a while the screen will freeze, I will be booted from my Vnc session and prompted with "read/select: Connection reset by peer (10054)". This wouldn't be so bad, but I can't reconnect to my Linux box. 

And upon closer inspection, it turns out that when this happens, my linux box is frozen after every occurrence. I can't input anything or do anything to unlock it. I have to hard reset it to get it up and running again.

Any ideas on what's going on?

---

### Post by Mr. C. on 2007-03-09
I don't think this is killing the kernel, but the graphical environment.  You can restart the graphical environment - no need to reboot, and definitely a bad idea to just power cycle.

Either ssh into your box, or use Ctrl-Alt-F2 to get to a terminal window.  Log in, and then:

sudo /etc/init.d/gdm restart

That will reload the graphical environment.

Now, as to why your VNC is crashing, I have no answers there.  Apparently RealVNC solved the issue last year in the 4.2.1 Enterprise Edition.  Change probably haven't made it back to the community.

Sorry,
MrC

---

### Post by VeganZombie on 2007-03-10
I've recreated the lock-up issue on my laptop and tried the Ctrl+Alt+F2 sequence but I still didn't get a response. 

I read somewhere that I can use the x11 vnc, but I want some assurance before I proceed.

---

### Post by Mr. C. on 2007-03-10
Well, that is unfortunate.  If you cannot gain access to a terminal via key sequence, perhaps there is something more problematic.  There is no harm trying to connect with VNC; I just doubt anything will come of it.

If you have another system in your LAN, you can try to remote connect if you have SSH running, or try to ping the laptop.  If there is no response, the lockup will require a reboot.

These are tough to diagnose.  It could be a driver bug, persistent hardware problem, or even a kernel bug.  I wish I had an easy answer for you; to identify the issue, you'll have to use a trial-and-error method.

Let's start with software - is your software up to date?

MrC

---

### Post by VeganZombie on 2007-03-12
Sorry for the late response -

Yes I do believe my laptop has all of the latest updates, and I'm running vnc3 on it because vnc4server seems to be problematic as of late. My Windows box is running the latest VNC viewer.

Side note: I think it'd be best to forego a long diagnosis phase. My laptop basically sits on the side of my desk anyway, I only VNC in to get around the botched keyboard on my laptop that forces me to plug in an external one, which completely defeats the purpose of having a laptop.

---

