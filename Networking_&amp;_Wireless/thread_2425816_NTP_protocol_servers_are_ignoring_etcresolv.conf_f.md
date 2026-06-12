---
title: "NTP protocol servers are ignoring /etc/resolv.conf for their DNS lookups"
date: 2019-08-31
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2019-08-31
i have discovered that the [COLOR=#0000ff][FONT=courier new]ntp[/FONT][/COLOR] server (network time protocol) was doing its DNS queries to the wrong IP address (and not getting any answers).  the [COLOR=#0000ff][FONT=courier new]/etc/resolv.conf[/FONT][/COLOR] file lists other IP addresses (not on my hosts).  _other programs are querying the correct addresses_.  i recently **un**installed [COLOR=#0000ff][FONT=courier new]ntp[/FONT][/COLOR] and installed [COLOR=#0000ff][FONT=courier new]openntpd[/FONT][/COLOR] (from the OpenBSD project).  _it, too, does the wrong DNS queries_.  i have not changed [COLOR=#0000ff][FONT=courier new]/etc/nsswitch.conf[/FONT][/COLOR] and nothing odd appears to be in there.  the queries are going to [COLOR=#0000ff][FONT=courier new]127.0.0.1[/FONT][/COLOR].  i have searched the [COLOR=#0000ff][FONT=courier new]/etc[/FONT][/COLOR] tree and found nothing that would seem to direct anything to [COLOR=#0000ff][FONT=courier new]127.0.0.1[/FONT][/COLOR] does anyone know what is going on and how to get these programs to use the specified DNS servers?  or do i need to run a DNS caching server at [COLOR=#0000ff][FONT=courier new]127.0.0.1[/FONT][/COLOR]?

---

### Post by wildmanne39 on 2019-08-31
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by SeijiSensei on 2019-08-31
I believe Ubuntu 18.04 uses [systemd-resolved]("https://manpages.ubuntu.com/manpages/bionic/man8/systemd-resolved.service.8.html") which listens on 127.0.0.53.  First run "ps ax | grep resolv" to make sure systemd-resolved is running on your system. 

If so, try changing the entry in /etc/resolv.conf to use 127.0.0.53 rather than 127.0.0.1. Any better?

On my 19.04 system, resolv.conf consists solely of these lines:

```

nameserver 127.0.0.53
options edns0
search mydomain.com

```

The last line is optional and simply adds mydomain.com to the end of any "unqualified" hostnames like "mylaptop" making it "mylaptop.mydomain.com".

---

### Post by Skaperen on 2019-08-31
[COLOR=#0000ff][FONT=courier new]/etc/resolv.conf[/FONT][/COLOR] does not have [COLOR=#0000ff][FONT=courier new]127.0.0.1[/FONT][/COLOR] at all.  it points to 3 offsite servers.  [COLOR=#0000ff][FONT=courier new]systemd-resolved[/FONT][/COLOR] is not running.  it was intentionally disabled back when i installed Xubuntu 18.04.  i didn't expect anything to use it since it is not referenced in [COLOR=#0000ff][FONT=courier new]/etc/resolv.conf[/FONT][/COLOR].  i want all DNS queries to go to the specified offsite servers.  how can i configure the 2 NTP programs to use those offsite servers listed in [COLOR=#0000ff][FONT=courier new]/etc/resolv.conf[/FONT][/COLOR]?

[COLOR=#0000ff][FONT=courier new]/etc/resolv.conf[/FONT][/COLOR]:
```

nameserver 209.244.0.4
nameserver 208.67.222.220
nameserver 1.0.0.1

```

---

### Post by Skaperen on 2019-08-31
i could install a local caching server if i can find one that can be configured to always forward to specified IP addresses.  any suggestions?

---

### Post by Skaperen on 2019-08-31
i found a candidate DNS caching server that can do forwarding called "unbound".

---

### Post by Skaperen on 2019-09-01
i have installed the [COLOR=#0000ff][FONT=courier new]unbound[/FONT][/COLOR] caching resolver, configured it to forward to 3 offsite servers (changed one of them), changed [COLOR=#0000ff][FONT=courier new]/etc/resolv.conf[/FONT][/COLOR] to go to [COLOR=#0000ff][FONT=courier new]127.0.0.1[/FONT][/COLOR] only so all programs use it (since is a local cache), and started it.  now things are working.  the logs show [COLOR=#0000ff][FONT=courier new]unbound[/FONT][/COLOR] reporting a lot of "[COLOR=#0000ff][FONT=courier new]bad udp cksum[/FONT][/COLOR]" on local queries but it seems to answer them, anyway.

the number of config options is [COLOR=#ff0000]*huge*[/COLOR].  "[COLOR=#0000ff][FONT=courier new]man unbound.conf[/FONT][/COLOR]" is [COLOR=#ff0000]*huge*[/COLOR] (_1186 lines_).

---

### Post by SeijiSensei on 2019-09-01
What happened to systemd-resolved?

Oh, you disabled it.

Does the machine get its configuration from DHCP? If so, systemd-resolved will use the servers specified there. You can also specify the servers in /etc/systemd/resolved.conf. [http://man7.org/linux/man-pages/man5/resolved.conf.5.html](http://man7.org/linux/man-pages/man5/resolved.conf.5.html)

Frankly I'd invest a bit of time learning to deal with systemd-resolved which is likely to be the standard mechanism for resolving names on Ubuntu for the foreseeable future.

---

### Post by Skaperen on 2019-09-01
that's probably a good idea, to some extent.  i was looking over some man pages a while back and its theory of operation just overwhelmed my retirement goal of taking it easy and letting others do the heavy stuff.  that's one of the reasons i moved my primary desktop over to Ubuntu.  at least this boots up and i can run far more compartmentalized virtual desktops than i have ever needed.

---

