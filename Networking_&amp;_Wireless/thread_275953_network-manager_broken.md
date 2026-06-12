---
title: "network-manager broken ?"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by ArneLovius on 2006-10-12
Just did a clean install of Dapper (PXE boot, then install direct from us.archive.ubuntu.com) on a Toshiba R100 (Centrino b/g laptop). Finished the install (with no errors), run sudo apt-get update and sudo apt-get upgrade which both completed, then went to Applications Add/Remove... and tried to install Network Manager.

The install completes, but at the very end it pops up a windows with 
"The network manager applet could not find some required resources, it cannot continue"

It doesn't put an icon/shortcut into Applications/Internet

I've had a quick google and found this [http://people.ubuntu.com/~fabbione/irclogs/ubuntu-motu-2006-05-08.html](http://people.ubuntu.com/~fabbione/irclogs/ubuntu-motu-2006-05-08.html) but I'm not sure what the relevance is, and what the 'fix' described in it is.

Cheers

---

### Post by High|ander on 2006-10-12
check in the /etc/network/interfaces 
it should contain:
```

auto lo
iface lo inet loopback

```

NOTHING ELSE!

When i did that, my nm-applet worked again :)

---

### Post by kingjere on 2006-10-15
Thanks, this was the answer I needed.

---

