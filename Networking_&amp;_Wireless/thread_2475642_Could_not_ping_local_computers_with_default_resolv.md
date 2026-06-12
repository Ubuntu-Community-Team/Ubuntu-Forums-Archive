---
title: "Could not ping local computers with default resolv.conf"
date: 2022-06-02
forum: Networking &amp; Wireless
---

### Post by yeahwhatever on 2022-06-02
I was not able to ping any devices on my local network even though my router has an internal DNS server, I kept getting "Temporary failure in name resolution" errors.  The problem seemed to be related to the /run/systemd/resolve/stub-resolv.conf file which was symlinked to /etc/resolv.conf.  This file had the following contents...

```
nameserver 127.0.0.53
options edns0 trust-ad
search .
```

I deleted the symlink and made a new file at /etc/resolv.conf containing this

```
nameserver 192.168.1.1
```

This solution worked and I'm able to ping all locally networked computers (and WAN domain names).  My question is...  why was /etc/resolv.conf symlinked to a non-working config file to begin with?  I really don't understand this setup and I'm worried my solution is ignoring something important.  Shouldn't Ubuntu be configured to properly resolve domain names out of the box?  Is there some type of risk with my solution that will come back to haunt me later on?  Simply put;  Is my solution a bad solution?  It seems to be working fine.

---

### Post by TheFu on 2022-06-02
> **yeahwhatever said:**
>  
This solution worked and I'm able to ping all locally networked computers (and WAN domain names).  My question is...  why was /etc/resolv.conf symlinked to a non-working config file to begin with?  I really don't understand this setup and I'm worried my solution is ignoring something important.  Shouldn't Ubuntu be configured to properly resolve domain names out of the box?  Is there some type of risk with my solution that will come back to haunt me later on?  Simply put;  Is my solution a bad solution?  It seems to be working fine.

Your solution is only temporary, I'm sad to say.  systemd-resolved is the problem.  symlinking /etc/resolv.conf to other locations has been happening on Ubuntu since around 2012 under resolvconf and then later when Canonical decided to use systemd-resolved.

systemd-resolved is local a caching DNS. This can be good and bad.  Alas, the more complicated something becomes, the easier it is to get mucked up.  The settings for that are stored in /etc/systemd/resolved.conf . You can see if there are any DNS and FallbackDNS settings in there.

For a desktop that doesn't move, you can disable, then mask, the systemd-resolved service.
```
sudo systemctl disable systemd-resolved
sudo systemctl stop systemd-resolved
sudo systemctl mask systemd-resolved
```
and it will never start again. It will never change your /etc/resolv.conf file either, which is more important. DHCP won't modify the resolv.conf either.  That's the downside, which may bite you in the future.

For laptops, not having DHCP with the ability to control the resolv.conf file settings can be bad much more often for obvious reasons.

It is your system.  Do what you like.  I run a pi-hole as a LAN DNS server and domain filter to block dangerous internet addresses. It runs in an LXD container - very light weight. This could be useful for you, since getting our phones and tablets and IoT devices to block all the nasty tracking isn't exactly easy without a DNS that we control.  Just something else to consider.

---

