---
title: "GUI with Unbuntu Server 9.10"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by RezRunner on 2010-02-13
Ok guys what I'm wanting to do is set up Ubuntu server on an older Dell x86 system it has 512 ram and 1.8ghz processor and a 40gig hard drive. I also want to have a GUI interface just to play with. I'm doing this all as a learning process to refresh what I know about Linux. I haven't messed with Linux since school and only used (Dare I Say) Redhat 7 at that time. Please let me know if this is possible.

Respectfully
RezRunner         :popcorn:

---

### Post by lukeiamyourfather on 2010-02-13
This is possible. Use this command to install GNOME and the basic set of applications that come with the standard version of Ubuntu.

```
sudo apt-get install ubuntu-desktop
```

It might take a little while because there are quite a few packages. If it doesn't bring up the graphical login when rebooting, you can get to the GUI with "startx" and end the graphical session with Ctrl+Alt+Backspace. Cheers!

---

### Post by RezRunner on 2010-02-13
So do you think the hardware is enough to do this?

---

### Post by jken146 on 2010-02-13
Yes, you can run GNOME on that. You might consider xubuntu-desktop if you want it to go a little faster. There are lighter options still, such as LXDE.

---

### Post by ikt on 2010-02-13
> **RezRunner said:**
> 512 ram and 1.8ghz processor and a 40gig hard drive.

Why not just install ubuntu desktop?

Those specs seem fine.

There's nothing special you can do in ubuntu server that you can't do in ubuntu desktop, besides maybe a few install options at the start.

---

### Post by 3rdalbum on 2010-02-13
> **ikt said:**
> Why not just install ubuntu desktop?

+1

Ubuntu Server is literally Ubuntu Desktop, minus the GUI.

Just install the regular Ubuntu Desktop and then use Synaptic Package Manager to install whatever server programs you want. It'll save you time and be easier on you.

Your system specifications are fine for installing Ubuntu Desktop or running a server.

---

### Post by The Cog on 2010-02-13
If it's a server, you will want to uninstall or disable avahi-daemon after installing the desktop or it will slow the server down horribly. With avahi running, every connection to the server takes maybe 5 seconds to respond. For a web server, that's not acceptable.

---

