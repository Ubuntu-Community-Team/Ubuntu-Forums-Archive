---
title: "cannot log out of Remote desktop session"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by wbsimey on 2014-06-11
We have a new Ubuntu server 14.04 system and are having issues with remote desktop (logging into Ubuntu from Win7).
so far we have:
installed ubuntu-desktop (sudo apt-get install ubuntu-desktop).
installed xrdp (sudo apt-get install xrdp).
I could login but screen was blank (grey) with no icons or menus.
installed fallback (sudo apt-get install gnome-session-fallback)
Still got blank screen.
installed xubuntu desktop (sudo apt-get install xubuntu-desktop).
had to add xfce4-session in place of . /home/user/.xsession to /etc/xrdp/startwm.sh
I could then log into Ubuntu, BUT, when I log out using the gui menu the desktop icons etc disappear, but the desktop background remains. I have to force quit remote desktop.
does anybody have a better way of setting up xrdp?
thanks,

---

### Post by TheFu on 2014-06-11
You are seeing a plain WM with your initial connections.  Tell the Windows machine to connect with a DE to see that at the start.
Or learn how to use a WM - try right clicking anywhere to see a simple menu. This menu can be customized - or you can choose to launch a different WM or complete DE. It is up to you.

I suspect that xrdp has an initial Xsession config which can be modified.  Sorry - don't know anymore than that - we use FreeNX on the server side. It feels 2x-3x more efficient than RDP or VNC-based desktops, plus it uses ssh for connection-security, so connections from anywhere in the world are secure, not just the LAN.

---

### Post by freddy4 on 2014-10-28
Hi wbsimey,
Did you ever figure out why when you log out using the gui menu the desktop icons etc disappear, but the desktop background remains.
I am having the same problem, any assistance would be appreciated.
Thanks

---

### Post by kapital2 on 2015-05-22
We have the same problem. After restarting the xrdp service with:
sudo service xrdp restart

the problem seems to be solved till the next restart (?)

---

### Post by steveferson on 2015-06-04
> **kapital2 said:**
> We have the same problem. After restarting the xrdp service with:
sudo service xrdp restart

the problem seems to be solved till the next restart (?)

I installed xrdp on my Lubuntu server about 2 years ago now and in that time have never had this working properly.

When I login everything appears fine, but when I click whatever the 'start' menu is called in Linux and logout, it just doesn't (works fine when I'm at the machine itself).

Instead, some of the icons change, it looks like something has changed within the DE like a specific module/package/something has been unloaded, but it won't log off.  I can repeat the action and nothing happens.

When I log back in again, I don't get the same session, but the previous one is still running (e.g. if I leave Firefox open in a session which I disconnect, I can't run it again when I reconnect cuz it's "already running")

I don't know if it's related but when I login I always get the error message "GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Cannot determine user of subject"

---

