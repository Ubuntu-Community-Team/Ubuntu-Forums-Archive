---
title: "Can't change global proxy hostname"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by amitst on 2007-04-11
Suddenly I have noticed that I am unable to change the global proxy settings through,
System -> Preferences -> Network Proxy. If I click "Manual proxy configuration" and try to change the text in HTTP Proxy edit box then a dialog with the following text is displayed.

--------------------------------
The application "gnome-network-preferences" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.

Clicking details button gives the following info
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/http_proxy/host' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/http_proxy/host' set in a read-only source at the front of your configuration path
--------------------

What might be wrong?

---

### Post by amitst on 2007-04-14
I got the solution.

I had put another proxy name in synaptic package manager proxy settings. This was preventing me to update the global proxy settings.

Thanks

---

