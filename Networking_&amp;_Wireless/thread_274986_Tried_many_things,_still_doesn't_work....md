---
title: "Tried many things, still doesn't work..."
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by NeoLithium on 2006-10-10
Hi All, 
Allrighty, after my initial install of Dapper; everything was perfect; even my network after using pppoeconf.  This morning; I upgraded to a higher speed DSL, which means I still go over pppoe, the only thing really different is the new phone line I have, and the fact that my login changed.

I changed the name by running pppoeconf again; but now it doesn't come up at boot; it runs the script; but I discovered that eth0 isn't active after I boot, I actually have to manually activate it.

Now, since it worked perfectly before, and I've reverted my config files back to their state that was before I started trying suggestions from other posts; unfortunately, nothing seems to work.  It just drives me nuts having to activate eth0 and run pon dsl-provider each time I log in.

I have a copy of the way /etc/network/interfaces is set up after I used pppoeconf (Aside from what the program edited, I haven't touched), and if you need anything else, just let me know.

Thanks!

```

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf

    iface eth0 inet static

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

# added by pppoeconf

auto eth0

```

---

### Post by NeoLithium on 2006-10-10
Ok, now that I've had a few more cups of coffee, I realize how dumb my post looks.  Tee Hee.  I should have had my eth0 set to dhcp....man I feel dumb.

Guess it's just one of those days ;)

---

