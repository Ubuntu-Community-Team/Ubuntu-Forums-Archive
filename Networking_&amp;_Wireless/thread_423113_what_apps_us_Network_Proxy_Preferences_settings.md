---
title: "what apps us Network Proxy Preferences settings???"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by rs98 on 2007-04-25
I am new to Linux/Ubuntu and one thing that confuses me is trying to get the OS and apps to properly access the Internet from behind a proxy server.  It seems like there is no one central place to specify proxy server settings (along with user and pass).

Which apps specifically use the info provided in the Network Proxy Preferences (System > Preferences > Network Proxy)?  As far as I can tell, the weather panel applet uses this info since I was only able to get updated weather info when I entered my proxy info.  Firefox seems to ignore this info and you have to enter it again in Firefox's preferences.

Are there other apps that make use of this info?  Does the info entered into the Network Proxy Preferences get exported as an env var (http_proxy)?  Does it get written to a .conf file somewhere?

I have played with a few Linux distros (Fedora, Gentoo, Ubuntu) and I would love to know if there is a way to specify proxy settings in one place and have all apps make use of that information.

---

### Post by spd106 on 2007-04-26
As far as I can tell the proxy settings are stored in gconf, so for an application to use these settings it will most likely have to be written to support gconf. This is mere speculation, but it may start you off in the right direction.

For Firefox I would like to see it able to use these settings as that would make it better integrated into the gnome desktop. For the moment I use the FoxyProxy plugin because it gives more fine grained control over proxies in FF.

---

### Post by rs98 on 2007-04-27
Thanks for the feedback.

I looked in the gconf dir and did not find any config files.

However, I did experiment with the Network Proxy Preferences and it definitely does export the env var $HTTP_PROXY with whatever proxy setting you specify.  So I guess if an app is setup to use the $HTTP_PROXY variable for HTTP access, then it will work.

---

