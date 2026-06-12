---
title: "Http_proxy set by installation, how to unset it?"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by xpista on 2008-08-09
Hi, 

  During the installation of the system (UB 8.04.1) on my notebook it asked me about the http proxy so I set one (which was valid at that time).

  Now when I am move my computer home (no http proxy needed) it seems that it remembers the value set. So when I do "sudo aptitude update" the system is trying to connect through the proxy from the installation. 

  I need to set "export http_proxy=" to bypass it.

  Question:
  _Where is the proxy information stored? How can I change/clean it?_ 
  I do not see it set in the environment variables.
  It's not visible through the gnome System/Preferences/Network proxy.
  Is it set only for aptitude/apt-get or for the whole system? (Firefox does not seem to be affected).
       
  
Thanks, Stefan

---

### Post by jimv on 2008-08-10
It should be set in System > Preferences > Network Proxy

---

### Post by xpista on 2008-08-10
> **jimv said:**
> It should be set in System > Preferences > Network Proxy

This does not work (as I mentioned before.)

The settings are initially set to "direct connection". 
The seting it to some random proxy and the back to the "direct connetion" does not work either.

The only program being affected seems to be aptitude/apt-get. The others work fine (Firefox, wget).

Stefan

---

### Post by xpista on 2008-08-10
Ok, I found it.
I was "apt" specific and it was set in /etc/apt/apt.conf.
I deleted the proper line in the config file and everything is OK now.

Stefan

---

