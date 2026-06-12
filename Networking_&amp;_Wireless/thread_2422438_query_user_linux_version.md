---
title: "query user linux version"
date: 2019-07-07
forum: Networking &amp; Wireless
---

### Post by terranz on 2019-07-07
I don't know if this is the right place but I don't know enough to ask the right question of google it seems.

on windows I can ```
query user /server:[computerDNSname]
``` and I can log a user off using the logoff command with the session ID but I don't know how to do it from linux.  It is a windows domain network and I'm running linux from my portable HDD.  When I'm logged in on a windows PC I have the rights to be able to do this.

---

### Post by TheFu on 2019-07-08
I don't know anything about Wndows.

If you want to logoff using a terminal session or ssh, use the <cntl>-d key or type **exit**.

If you have an X/Session and want to logoff, kill the X/session.  **sudo killall Xorg**  This won't cleanly cost running programs and any child programs will be terminated.

If you want to do the same on remote computers, then just ssh into each computer and kill the display manager.  

google found this: [https://www.cyberciti.biz/faq/linux-logout-user-howto/](https://www.cyberciti.biz/faq/linux-logout-user-howto/) - that is a reputable website, assuming the tip is for the specific release you are using.

I have no idea how to do this if Wayland is being used for the display manager.

---

