---
title: "CPU &amp; Memory Use (Jaunty)"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by MaxVK on 2009-07-16
Hi. Iv been watching my CPU and Memory usage in jaunty and I'm curious about a couple of things:

I have my screen saver disabled, but in the System monitor I can see Gnome-Screensaver, and every so often it kicks in and uses CPU/Memory although I'm using the machine at the time and the screensaver never starts in any case. How can I remove it from running in the background?

What is gvfsd? Its there too, along with a bunch of other entries. What does it do, is it required and can I stop it if its not?

What is the seahorse-agent? Again, it uses memory and cpu here and there and actually makes a difference to the performance when it does. Is it required and how can I turn it off if its not?

Cheers

Max

---

### Post by Mornedhel on 2009-07-16
> **MaxVK said:**
> I have my screen saver disabled, but in the System monitor I can see Gnome-Screensaver, and every so often it kicks in and uses CPU/Memory although I'm using the machine at the time and the screensaver never starts in any case. How can I remove it from running in the background?

I don't know how to do this without potentially breaking things when you decide to lock your computer while you're away for coffee. I'm interested in a solution that lets you disable gnome-screensaver at all times unless explicitly summoned, though.

> **MaxVK said:**
> What is gvfsd? Its there too, along with a bunch of other entries. What does it do, is it required and can I stop it if its not?

Gnome virtual file system daemon. It's the daemon that exposes (S)FTP, SMB, etc. mounts to the gio interface, which in turn is used by most Gnome applications in e.g. Open File dialogs. I would not stop it.

> **MaxVK said:**
> What is the seahorse-agent? Again, it uses memory and cpu here and there and actually makes a difference to the performance when it does. Is it required and how can I turn it off if its not?

Lets applications (for instance NetworkManager) access keyrings when needed. Better not stop it either.

Well, technically, all of those are stoppable without borking your system, but you'd lose important functionality.

---

### Post by MaxVK on 2009-07-16
Thanks Mornedhel, at least I know not to stop them now, but its a pain about the screensaver thing, since these three seem to take up much more CPU and memory when they start doing something.

Oh well. Ill keep an eye on this thread just in case someone comes up with something devastatingly clever to turn off everything that is not explicitly needed by the system.

regards

Max

---

