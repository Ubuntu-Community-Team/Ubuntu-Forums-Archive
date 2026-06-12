---
title: "bare bones install"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by dimitriv on 2009-02-23
Hi

I want to run Ubuntu as a host and as a guest virtual machine. The host would run all my apps, while the guest VM would be used soley for some internet activity (requiring only internet apps i.e. FF, Skype and a few others). I want the VM guest to utilise smallest possible footprint (HDD space on host).
Using Add/Remove Applications on the guest I've removed some that can go. Many are part of Synaptic Packages, using the manager I'm unsure what can go or must stay. Can anyone please advise on how to make a bare bones install that will allow some internet apps to work (with most other stuff removed).
Appreciate any suggestions

Thanks

---

### Post by skymera on 2009-02-23
Using the alternate CD you can install a "Command Line System"
This is very minimal

---

### Post by dimitriv on 2009-02-23
as mentioned i need to run a few apps like FF & Skype etc. that require the UI (and i need a UI...)
thanks for the comment

---

### Post by 3rdalbum on 2009-02-23
The kind of thing I would suggest is to install JeOS (Just Enough Operating System) as the guest operating system. Don't worry about the name, it's just an extremely bare-bones Ubuntu system. From there, you can install Network Manager (if needed?), xserver-xorg, Openbox (window manager) and your web applications like Skype, Firefox etc. You will also need a login manager too. XDM should be able to do the job and be very lightweight, otherwise you can use GDM.

It's better to start from a slim base and add to it, than start with a fat system and trim stuff out of it.

If you do need to go about the other route of just trimming stuff from your existing guest installation, use the virtual machine's Snapshot function to create a snapshot before removing a package. That way, if the package removal breaks the system, you can just roll back to the last snapshot.

---

### Post by Doug11 on 2009-02-23
What about something like DamnSmallLinux,,small and light weight? There are a few other lightwieght distros.

---

### Post by theozzlives on 2009-02-23
you can run all that from the host and save disk space, memory, and trouble. Unless you just wanna do it "because you can".

---

### Post by dimitriv on 2009-02-24
thanks for the comments

JeOS looks like it's intended for server (would it run on a desktop host?), also slightly concerned by

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)
# No graphical environment preloaded as it is aimed at server virtual appliance
# Working knowledge of linux administration and debian packages recommended to start building your own appliance

will also look at DSL

Thank you

---

