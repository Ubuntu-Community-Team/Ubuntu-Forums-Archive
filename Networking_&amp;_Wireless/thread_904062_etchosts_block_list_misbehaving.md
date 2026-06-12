---
title: "/etc/hosts block list misbehaving"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by tolmeda on 2008-08-28
After implementing a block list with /etc/hosts, I'm seeing strange behavior with name resolution. For example, the new /etc/hosts file contains the following entry:

```
0.0.0.0 att.com
```

After a reboot, I get this when I ping it:

```
$ ping att.com
PING att.com (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.032 ms
```

And Firefox goes directly to the site with no problem. So, why is Firefox ignoring /etc/hosts entries and why does it resolve to 127.0.0.1 when I ping it instead of 0.0.0.0?

---

### Post by Iowan on 2008-08-29
It may depend on how your system does lookups.  If it checks DNS before hosts... (/etc/nsswitch.conf?)

---

### Post by tolmeda on 2008-08-31
Here is the contents of my /etc/nsswitch.conf file:

```
passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

If I understand it correctly, it should be looking at /etc/hosts for name resolution first.

I'm still baffled by this.

---

### Post by caljohnsmith on 2008-08-31
I think 0.0.0.0 has special meaning in networking, so you can't use it; if you just want some bogus IP, try 1.1.1.1 as the IP. I know that works in /etc/hosts.

---

### Post by tolmeda on 2008-08-31
I think I'm getting the correct behavior from the command line now. I changed /etc/hosts to use 127.0.0.1 as the dummy address. Also changed /etc/nsswitch.conf as follows:

```
...
hosts:          files dns
...
```

All is okay (resolved to 127.0.0.1) when I ping att.com for example.

But, in a browser (tested with both Firefox and Opera) I still get to the actual web site so name resolution is working correctly... which is incorrect in this case.

Could it be affected by my proxy configuration in Gnome? Gnome is configured to use a proxy for all protocols. Would it proxy the name resolution too?

---

### Post by tolmeda on 2008-09-02
I pretty sure this is a Gnome proxy problem. I tested at home last night with proxy configuration turned off and entries in my /etc/hosts block list correctly resolved to 127.0.0.1 in both command line apps and desktop apps.

But again today at the office with proxy configuration turned on, requests from desktop apps (Firefox, Opera) are not resolve based on the /etc/hosts file and are instead resolved to their actual ip addresses.

Anyone have any ideas on how to fix this?

---

### Post by caljohnsmith on 2008-09-02
> **tolmeda said:**
> I pretty sure this is a Gnome proxy problem. I tested at home last night with proxy configuration turned off and entries in my /etc/hosts block list correctly resolved to 127.0.0.1 in both command line apps and desktop apps.

But again today at the office with proxy configuration turned on, requests from desktop apps (Firefox, Opera) are not resolve based on the /etc/hosts file and are instead resolved to their actual ip addresses.

Anyone have any ideas on how to fix this?
Just an idea, but have you considered putting a simple local proxy on your computer like Dansguardian, and then configure that to use your external proxy? With Dansguardian you can block any sites you want to, and it is much more configurable then simply putting hosts in /etc/hosts to block them.

---

