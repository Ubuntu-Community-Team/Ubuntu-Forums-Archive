---
title: "Proxy hell"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by thammr on 2008-10-07
I understand that proxies for Package Manager and apt-get can be setup in several ways. The thought of putting my proxy (with password) in an environment variable seems absurd to me. The thought of putting my password in plain text in apt.conf is only slightly less objectionable. 
Since I upgraded to the most recent version of UBUNTU I've had untold problems with proxies. I can get updates and use the Package Manager but apt-get fails.
Today I discovered one cause. Something is creating an environment variable

http_proxy=http://:8080/

I can't find out where this is being set. So to use apt-get, I open a command window, delete http_proxy and then use apt-get. After this, things like "sudo apt-get update" works properly.

Anyone know how to stop http_proxy from being set?

---

