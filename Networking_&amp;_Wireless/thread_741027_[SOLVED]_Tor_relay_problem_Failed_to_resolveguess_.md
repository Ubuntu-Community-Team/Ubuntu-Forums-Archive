---
title: "[SOLVED] Tor relay problem: Failed to resolve/guess local address."
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by stretch44 on 2008-03-31
I'm running Xubuntu 6.10, and have configured Privoxy and Tor.  I have the Firefox "TorButton" loaded, so I can turn on Tor as a client while browsing.  Works great!

So, I thought I'd do my part for the Tor network, and configure my laptop to work as a Tor relay.  I change 3 things in the /etc/tor/torrc file:
1) I give myself a Nickname
2) I give myself some ContactInfo
3) I set ORPort to some unused port like 60002

I then go to my wireless router, which has given me a private IP address of 192.168.1.102, and I forward port 60002.

I should now be ready to roll.  Here's what the message I get from the command line when I restart Tor.  (My machine's name is "lombard"):

```
user@lombard:~$ sudo /etc/init.d/tor restart
Stopping tor daemon: not running (there is no /var/run/tor/tor.pid).
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
Mar 31 11:33:23.403 [notice] Tor v0.1.1.23. This is experimental software. Do not rely on it for strong anonymity.
Mar 31 11:33:23.409 [notice] resolve_my_address(): Guessed local hostname 'lombard' resolves to a private IP address (127.0.1.1).  Trying something else.
Mar 31 11:33:23.410 [notice] resolve_my_address(): Interface IP '192.168.1.102' is a private address too.  Ignoring.
Mar 31 11:33:23.410 [warn] resolve_my_address(): Address 'lombard' resolves to private IP '127.0.1.1'. Tor servers that use the default DirServers must have public IP addresses.
Mar 31 11:33:23.410 [warn] Failed to parse/validate config: Failed to resolve/guess local address. See logs for details.
Mar 31 11:33:23.410 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.

```

It gets the private address correctly... but it doesn't seem to know how to resolve it's public address.  I assume the problem is that it doesn't know the Default Gateway address.  (?)

Any ideas on where to go from here?
Thanks,
stretch44

---

### Post by stretch44 on 2008-03-31
update: Playing around with the torrc file, I've found that hard-coding my public IP address (after a quick check to whatismyip.com) gets the job done.

So Xubuntu continues to be working with the adapters properly, etc.  This is more of a problem relating to Tor's handling of dynamic IPs.  That is, Tor [by default]("https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#DynamicIP") detects your IP address, and it's not doing a very good job on my system.  Hard-coding is a short-term solution; I doubt Tor will continue to list me as a relay once my ISP changes up my IP.

I'll mail the or-talk mailing list for help later, but if anybody has an easy answer (or suggestion), by all means, feel free to chime in.  =)

stretch44

---

### Post by stretch44 on 2008-03-31
My architecture [ppc] and suite [edgy] of Xubuntu constrain me to Tor version 0.1.1.23-1 from apt-get.

There are newer versions of Tor available though.  What are the odds I can just grab a newer package and have it work?  Would attempting this cause issues that "apt-get --purge remove tor" couldn't undo?

---

### Post by stretch44 on 2008-04-02
For the record, loading the newest, unstable version of the software from source fixed everything.  Relay running fine.

---

