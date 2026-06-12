---
title: "resolv.conf not keeping config"
date: 2004-12-14
forum: Networking &amp; Wireless
---

### Post by scook94 on 2004-12-14
I've been having problems with DNS and my broadband router (as posted previously), so I've been trying to resolve it from the info posted here -
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

However, I seem to be experiencing the same as this post -
[http://ubuntuforums.org/showthread.php?t=7280](http://ubuntuforums.org/showthread.php?t=7280)

Sadly for me the fix in this last post doesn't seem to be working for me.
When I shutdown Ubuntu one of the lines I see states something along the lines of
Deconfiguring  network interfaces.

I'm guessing that this is where my resolv.conf is being changed and where I'm losing the DNS entries I've made.
Anyone have any ideas I can try? It's getting old having to re-enter my DNS servers so I can access the web, if I can't get it resolved I'm gonna try another distro for my laptop...  :(  ](*,)

---

### Post by mpjbrennan on 2004-12-26
I got my settings to persist by commenting out the function make_resolv_conf() in /etc/dhcp3/dhclient-script.

patrick

---

