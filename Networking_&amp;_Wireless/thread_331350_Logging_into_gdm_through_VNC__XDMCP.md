---
title: "Logging into gdm through VNC / XDMCP"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by Omegatron on 2007-01-04
I'm using a fresh install of 6.10.  I tried to follow the directions from this thread (including the port forwarding for XDMCP in my router), but they don't seem to work:

[http://ubuntuforums.org/showthread.php?t=42941&page=9#86](http://ubuntuforums.org/showthread.php?t=42941&page=9#86)

However, I'm close:

[LIST]
[*]I can use VNC to log in through the Remote Desktop thing while I am logged into the remote computer already
[*]When the remote computer is at the login screen, I can use XDMCP to log in from another Ubuntu installation's login screen
[*]But when the remote computer is at the login screen, trying to connect to it with VNC does nothing.
[/LIST]

So it must be a problem with the vnc4server?  Does this work correctly in 6.10 with the /etc/inetd.conf settings [described in that thread]("http://ubuntuforums.org/showthread.php?t=42941#td_post_220338")?  I typed **sudo /etc/init.d/inetd restart** as described and it did nothing, so something's different between versions...

---

