---
title: "Feisty + IPv6 ifup failure"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by nautilus on 2007-04-15
I've found something interesting.

When configuring an interface with IPv6 as such:

```
# The primary network interface
auto eth0
iface eth0 inet static
        address         192.168.0.200
        netmask         255.255.255.0
        gateway         192.168.0.1
iface eth0 inet6 static
        address         2001:470:1f00:488:1::200
        netmask         80
        gateway         2001:470:1f00:488:1::1

```

At the point where ifup attempts to setup the IPv6 portion, it does this:

```
$ sudo ifup -nv eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d

ifconfig eth0 192.168.0.200 netmask 255.255.255.0               up
 route add default gw 192.168.0.1  eth0
run-parts --verbose /etc/network/if-up.d
Configuring interface eth0=eth0 (inet6)
run-parts --verbose /etc/network/if-pre-up.d
modprobe -Q ipv6
ifconfig eth0    up
ifconfig eth0 add 2001:470:1f00:488:1::200/80
 route -A inet6 add ::/0 gw 2001:470:1f00:488:1::1 eth0
run-parts --verbose /etc/network/if-up.d

```

However, the line: **modprobe -Q ipv6** fails, since the IPv6 module does not exist, because I have compiled IPv6 support directly into my kernel.

Interestingly, the modprobe manpage defines the -Q flag as 'silent', meaning it should never generate an error, but for some reason it returns false if a module does not exist:

```
$ if `modprobe -Q evdev`; then echo True; else echo False; fi
True
$ if `modprobe -Q ipv6`; then echo True; else echo False; fi
False

```

Anyway, this is the point where my ifup attempt fails due to error, and I would normally hack an up line into the ipv4 config portion of my interfaces file to append ipv6 addresses and setup routes and such.

But really, this is a bug in modprobe, right?

I've looked through the source (from apt-get source modprobe) and have found no --silent flag, so I was left assuming it was in module-init-tools, which I have poked around within without much direction, and so far haven't found what I'm looking for.

Any coders around who know where this --silent flag comes from?

Besides that:

```
modprobe.c +1171

#ifdef COMBINE_modprobe
                if (runit) {
                        int insmod_main(int argc, char **argv);
                        int flag_autoclean_save = flag_autoclean;

                        flag_autoclean = 0;
                        ret = insmod_main(my_argc, my_argv);
                        flag_autoclean = flag_autoclean_save;
                }
#else
                if (runit)
                        ret = xsystem(my_argv[0], my_argv);
#endif /* COMBINE_modprobe */
                if (!quiet && ret != 0)
                        error("insmod %s failed", desc->nod->str);
        }

        /*
         * post-install
         */
        for (p = desc->name; ret == 0 && p; p = p->next) {
                const char *name = p->item.s;
                if ((ex = exec_cmd(EXEC_POST_INSTALL, name)) != NULL) {
                        verbose("# post-install %s:\n%s\n", name, ex);
                        /* Trusting commands from config file */
                        if (runit && (ret = system(ex)) != 0)
                                error("post-install %s failed", name);
                }
        }

        if (ret == 0)
                *new_in_kernel = linkit(FIRST, desc, *new_in_kernel);

        readcur();
        return ret;
}

```

Shouldn't it return /prior/ to attempting a post-instal upon failure?

---

### Post by nautilus on 2007-04-18
I actually didn't notice the:

```
route -A inet6 add ::/0 gw 2001:470:1f00:488:1::1 eth0
```

which ifup does... that's very incorrect...

The reason this doesn't work is because if this were a router doing SIIT translation, it would map IPv4 addresses into IPv6 as such: ::66.124.2.12

By that configuration, these IPv6 mapped IPv4 addresses would then be routed to the upstream gateway, which would shrug and discard them as unroutable or, worse, route them through its own SIIT!

The correct way of specifying a default route is with 2000::/3, not ::/0

By not doing this properly, many installations are going to be quite broken in the near future...

---

### Post by nautilus on 2007-05-04
Well, it's been a month or so, so I dove in and fixed the issue with my own monkey-like paws.

[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/107448](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/107448)

[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/107432](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/107432)

Patches linked on Launchpad.

---

