---
title: "Zesty DNS resolution no longer accepts search domain setting from DHCP"
date: 2017-09-04
forum: Networking &amp; Wireless
---

### Post by goatboy73 on 2017-09-04
This is on Ubuntu Gnome 17.04 (fully updated), btw...

As we all know, Zesty's name resolution changed from dnsmasq (via NetworkManager) to systemd-resolved. One side effect (that apparently 17.10 already fixes) is that DNS resolution for local names (i.e. non-fqdn) only uses local MDNS, instead of using DHCP's DNS servers.

After much reading, I've come to realize that the problem here is due to systemd-resolved's default behavior. However, all the remedies I've found mention creating a .network file with specific contents (see below), putting it in /etc/systemd/network, and re-starting.

This is what I've done so far:

```

# cat /etc/systemd/network/usedomains.network
[Match]
Name=en*

[DHCP]
UseDomains=yes

```

Now, I've tried it both with and without the [Match] section, as well as the specific ethernet interface name, MAC address, etc. No dice. Under no circumstances does the resolver pick up the domain setting from DHCP.

Needless to say I have other older boxes which have no such issue.

I believe the issue has to do with using NetworkManager to continue to manage the network stack, vs. using systemd-networkd - so apparently it's NetworkManager "somehow" failing to tell systemd-resolved that it should use the DHCP domains.

The reason I've been reluctant to switch to systemd-networkd is because I don't want to mess around too much with the default Ubuntu layout. In particular, I don't want to break the GUI-related stuff (what can I say? I've become lazy in my late years :D).

This is the current behavior (where the DHCP-configured DNS servers aren't used, and the DHCP-configured domain name isn't used as a search domain for local names):

```

# dig +short some-local-hostname
(no record found)

```

This is the desired behavior (where the DHCP-configured DNS servers are used, and the DHCP-configured domain name is used as a search domain for local names):

```

# dig +short some-local-hostname
192.168.XXX.XXX

```

So...anyone wish to chime in? Any thoughts on how I might be able to fix this annoying little issue?

---

