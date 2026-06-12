---
title: "How to force an application to use a proxy"
date: 2017-06-23
forum: Networking &amp; Wireless
---

### Post by alireza-crs on 2017-06-23
Hi.
  As far as I know, using a proxy by setting system variables is just a  request to the app to use proxy, and the app can simply ignore it.

  So my question is: Is there anyway to FORCE some application to use a proxy?
I tried setting proxy from gnome control center but it didn't work.

---

### Post by TheFu on 2017-06-23
Never forget that Linux is multiuser.

You can for an entire machine to use a transparent proxy.

You can force a specific userid or groupid to have specific iptables rules.  

Trying to match on an application name is useless. There are 5,000 ways around it for any user on the machine if they have any network access.

I don't know how to force 1 specific application to use a proxy, however.  Might be away to do it through firejail or another container technique - but this would be similar to to the application-name matching technique. It would be trivial to get around if someone wanted.

The whole machine proxy is the only certain method, IMHO. Lots of how-tos for that.

---

### Post by papibe on 2017-06-23
Hi alireza-crs.

Take a look at [proxychains]("http://glug.nith.ac.in/blog/how-to-proxify-application-and-apt-get-in-ubuntu-using-proxychains/").

I haven't tried myself, so you need to explore it further.

Regards.

---

