---
title: "Remmima under WSL (Windows Subsystem for Linux)"
date: 2020-09-26
forum: Networking &amp; Wireless
---

### Post by benjaminbreeg on 2020-09-26
Has anyone managed to make Remmima work under WSL? I installed Focal Fossa in WSL, and then added Remmima. When attempting to launch Remmima in the WSL terminal, here's what I am getting:
```
benjaminbreeg@DadsHP:~$ remmina
xprop:  unable to open display ''
xprop:  unable to open display ''
Remmina plugin glibsecret (type=Secret) has registered but not yet initialized/activated. Initialization order is 2000.
[glibsecret] unable to get secret service: Cannot autolaunch D-Bus without X11 $DISPLAY
Unable to init server: Could not connect: Connection refused

(org.remmina.Remmina:4565): Gtk-WARNING **: 14:27:57.391: cannot open display:
```
What am I doing wrong please? Is that how you launch Remmima in command line mode?

---

### Post by TheFu on 2020-09-26
Unix systems require a compatible display server to work.  That usually means X/Windows.  WSL doesn't provide that.  Commercial options are usually about $150 for Windows.  Linux desktop distros include the F/LOSS X/Server.

For most people stuck with Windows, running a desktop Linux inside a virtual machine is the easy answer.  

People like me run Windows inside a VM under linux so we have much more control.  If you do that, then remmima isn't needed as remote X11 is built into all Unix desktops the last 30-40 years. Accessing Unix systems from around the world has been possible a very long time. I've managed servers in Japan, Nepal, Korea, South Africa and across the Americas (north, central and south) remotely for a long time. 99.9% of te time, I use ssh, but when needed remote X11 can work.

---

### Post by benjaminbreeg on 2020-09-27
> **TheFu said:**
> Unix systems require a compatible display server to work.  That usually means X/Windows.  WSL doesn't provide that.
Many thanks! That clears it! The easiest way I've managed to control Ubuntu remotely from Windows is via Chrome Remote Desktop, only [lately this has not allowed me to control the very session that's currently running on the remote desktop]("https://support.google.com/chrome/thread/73265328?hl=en"). Apparently [these instructions]("https://researchxuyc.wordpress.com/2014/07/30/to-show-the-same-display-session-in-ubuntu-by-chrome-remote-desktop/") do not work anymore.

---

### Post by TheFu on 2020-09-27
I won't allow google-chrome on my systems. I care about privacy.
If you want to control Linux/Unix systems, use ssh.

---

