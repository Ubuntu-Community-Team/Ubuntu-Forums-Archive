---
title: "Setting up squid"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by auraithx on 2008-03-26
Trying to use this tutorial to set up squid but it seems out-dated and doesn't work correctly with the current version.

[http://www.tldp.org/HOWTO/TransparentProxy-4.html](http://www.tldp.org/HOWTO/TransparentProxy-4.html)

ie:

```
mark@mark-desktop:/etc/init.d$ sudo squid -z
2008/03/26 22:00:49| parseConfigFile: line 3005 unrecognized: 'httpd_accel_host virtual'
2008/03/26 22:00:49| parseConfigFile: line 3006 unrecognized: 'httpd_accel_port 80'
2008/03/26 22:00:49| parseConfigFile: line 3007 unrecognized: 'httpd_accel_with_proxy on'
2008/03/26 22:00:49| parseConfigFile: line 3008 unrecognized: 'httpd_accel_uses_host_header on'

```

---

