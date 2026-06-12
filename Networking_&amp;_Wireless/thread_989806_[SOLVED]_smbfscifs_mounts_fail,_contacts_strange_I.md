---
title: "[SOLVED] smbfs/cifs mounts fail, contacts strange IP address"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by advoss on 2008-11-22
I execute a command such as: ```
"sudo mount -t cifs -o username=(removed),password=(removed),uid=(removed),gid=(removed) //FOO/Public /mnt/samba/foo"

```

Which used to work fine, but now times out (mount error 110)

In trying to research a solution I found suggestions for running smbtree.
For both windows and linux boxes the output is:
```
	\\FOO            		
timeout connecting to 216.24.138.136:445
timeout connecting to 216.24.138.136:139
cli_start_connection: failed to connect to FOO<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED

```

I notice the ip address that is trying to connect to also appears when I run the mount command verbosely.
```
parsing options: rw,username=(removed),password=(removed),uid=(removed),gid=(removed)

mount.cifs kernel mount options unc=//FOO\Public,ip=216.24.138.136,ver=1,rw,username=(removed),password=(removed),uid=(removed),gid=(removed) 

```

Whois.net look up attributes that ip address to "ViaWest Internet Services, Inc."  which I know nothing about.

The workstations in the smbtree are all on the LAN and do not have static ip addresses.

Why is the command accessing the internet?  How do I mount my shares?

Thanks,
advoss

---

### Post by advoss on 2008-11-22
Ultimately the solution required [re]installing winbind and configuring [re]configuring nsswitch.conf.  I also discoverd that the set dns servers would resolve anything not found to 216.24.138.136, i changed to different name servers to hopefully end such behavior.

---

### Post by kurtpete on 2008-11-24
> **advoss said:**
> Ultimately the solution required [re]installing winbind and configuring [re]configuring nsswitch.conf.  I also discoverd that the set dns servers would resolve anything not found to 216.24.138.136, i changed to different name servers to hopefully end such behavior.

I have the exact same strange behavior, including anything not found resolving to 216.24.138.136.  Who is your internet service provider, if I may ask?  I have mediacom, and I am using the dns servers supplied by them via dhcp.  I may manually change, though.  This isn't expected (or desired) behavior...

---

