---
title: "Is RDesktop only for Ubuntu-Windows?"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-07-11
I have my laptop and desktop here. Both 64 bit install of Hardy Heron. Laptop wirelessly, Desktop wired.

I just tried to rdesktop to the laptop and it said connection refused. I did the same with laptop TO desktop. Same error. On both, remote desktop connection is enabled.

I went to applications-internet-remote desktop viewer, and it worked then. But I almost kind of miss the whole rdesktop 192.168.x.x and BAM, it's there.

Can I get it to work with Ubuntu-Ubuntu? Everywhere I look everybody refers to it as Ubuntu's answer to remote in to Windows...

---

### Post by spd106 on 2008-07-12
The underlying technology (VNC) is cross platform, so it will work on any Windows, Mac or Linux machine as long as you have the VNC server software enabled (see System -> Preferences -> Remote Desktop).

It's most common to use this when connecting to Windows because it's much quicker and easier to use SSH for a remote shell to administer a *nix box.

---

