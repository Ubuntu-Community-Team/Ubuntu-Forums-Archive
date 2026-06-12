---
title: "Allowing internet only to one website"
date: 2022-07-10
forum: Networking &amp; Wireless
---

### Post by bobox2 on 2022-07-10
Hi there,

I am setting my son's first PC and would like him to start with Ubuntu instead of Windows.  I have the admin account on the PC and he has a custom user account. I want him to be able to access only one website - that of his school where he can find his homework, etc.

I have set up a private key to be able to log on the machine even from another Windows machine with Putty and can switch off remotely the access to the network with these

sudo nmcli networking off 
sudo nmcli networking on

However, I would like to allow him to access this website address. All the rest should be off.
Is there a way to do that? I am thinking of using UFW possibly?

Thanks in advance
Bob

---

### Post by TheFu on 2022-07-10
You can setup a whitelist of allowed location by disabling DNS and only using /etc/hosts to resolve hostnames.  This isn't perfect and will break all sorts of things, like patching and keeping time, but you can do it.
There are ways around DNS failures, so depending on the age/capabilities of you son, DNS might not be sufficient.  What will work for a 7 yr old, won't work for a 15 yr old.

Another method is to setup a pi-hole and place his computer into a separate group that has massively filtered DNS results based on the MAC or hostname.  Today, I'd use this method. I run a pi-hole instance inside an LXD container on 2 of my physical machines to provide filtered DNS to my entire network.  I'm using it for blocking ads, but there are blocklists for lots of things - like parental controls.

Some DNS providers will allow something similar through DNS accounts, some are free.  Check out openDNS for their available filters.

If you want a fool-proof method, then you'll need to rearrange your network so that there is a proxy server and only the proxy server has internet access. No regular clients get access, except through the proxy.  The restricted clients cannot even ping 1.1.1.1 (a well-known internet location).  But if you still have Windows on your network, that will always be a back door to the outside world thanks to their IPv6 tunneling through IPv4 methods that are setup by default and don't like to be disabled. This effectively pierces any firewall setup.

I think you should reconsider the nmcli commands.  After you turn off networking, you won't be able to ssh into the system to re-enable it.

While you are at all of this, you might want to consider
a) setting up time limits for access in your router, based on the client machine. Most current routers have schedule access software.
b) get a $20 cheapo wifi USB plug and setup only that plug for your son's use.  When it is time to punish/restrict internet access, then you can take that tiny wifi adapter away and lock it up. That's a clear punishment which is easier for small humans to understand than a virtual "disabled" idea.  Plus, you can setup different filters for the internal connection than for the external wifi connection.

There's lots of accounting in all of this.  The internet isn't just http/https and it doesn't just work on a few ports. There are thousands and thousands of ports that are used by our systems.  How good the access restrictions need to be is something only you can judge.  I like the whitelist host lookups for under 10 yr olds. No need to enable/disable networking.

---

### Post by mIk3_08 on 2022-07-11
> **bobox2 said:**
> 
However, I would like to allow him to access this website address. All the rest should be off.
Is there a way to do that? I am thinking of using UFW possibly?
Bob
I think this can be configured via router. I have tried this one on Linksys router wireless G and block websites then enable only few websites at your end. I have tried this long time ago. I don't know if this is still available to the Linksys router nowadays. Maybe they still have those configurations available. Just check it out. Anyway, when buying a router just see the specifications and capabilities of it so you will be able to configure the router based on your needs at your end. Regards and cheers.

---

