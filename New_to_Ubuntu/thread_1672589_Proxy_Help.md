---
title: "Proxy Help"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by klossor on 2011-01-21
Hey all, I'm looking for a system-wide proxy solution for a fresh install. I've added a regular proxy which works with the web browser, but all other apps (Xchat, Kopote, Jabber client etc) seem to ignore the proxy.

Also during IRC login on xchat, with the proxy details added manually to the irc client, logon to the network is denied. Is there any proxies that work easily with irc servers?

Any help on this would help, thanks ;)

---

### Post by klossor on 2011-01-21
Anyone got any idea's at all? I'll take a long shot at this stage :D

---

### Post by Dr Small on 2011-01-21
You could use this guide and work out a solution:
[http://ubuntuforums.org/showthread.php?t=1078033&highlight=transproxy](http://ubuntuforums.org/showthread.php?t=1078033&highlight=transproxy)

---

### Post by Riffer on 2011-01-21
Top left on the panel where your drop down menus are, click on System, then Preference and then Network Proxy.  In there you can configure your proxy settings, apply it to different protocols and make it system wide.

---

### Post by pl@yer on 2011-01-21
The standard way to set proxy used to be by setting an environmental variable called http_proxy. For some reason this does not seem to work anymore, you need to set by clicking system/preferences/network proxy .

---

