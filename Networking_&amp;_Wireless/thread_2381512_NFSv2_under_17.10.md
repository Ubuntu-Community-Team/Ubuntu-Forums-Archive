---
title: "NFSv2 under 17.10"
date: 2018-01-01
forum: Networking &amp; Wireless
---

### Post by paul-taniwha on 2018-01-01
Just upgraded my laptop to 17.10 and my normal embedded dev system that happily worked yesterday refuses to boot - it starts from uboot by loading a kernel from an NFS mounted filesystem on the laptop with:

  [FONT=monospace][COLOR=#000000]Loading: *** ERROR: File lookup fail[/COLOR]

poking around with wireshark shows me that it's failing because uboot is asking using NFSv2 and the server on the Ubuntu laptop only supports v3/4, checking in [/FONT] [FONT=monospace][COLOR=#000000]/proc/fs/nfsd/versions we get

[/COLOR][/FONT][FONT=monospace][COLOR=#000000]  -2 +3 +4 +4.1 +4.2[/COLOR]

So how do I turn NFSv2 back on on Ubuntu? searching the net shows lots of examples of now to turn it off, but none for turning it on[/FONT]

---

### Post by paul-taniwha on 2018-01-01
OK - I solved this myself - edit /etc/default/nfs-kernel-server

Change:

    RPCNFSDCOUNT=8

to:

    RPCNFSDCOUNT="-V 2 8"

And change:

    RPCMOUNTDOPTS="--manage-gids"

to:

    RPCMOUNTDOPTS="-V 2 --manage-gids"

then issue:

    sudo service nfs-kernel-server restart

---

### Post by j ferguson on 2018-12-08
Wow, Paul. I could have spent a week on this. THANKS.  I upgraded(?) from 16.04 to 18.04 and lost service from my HP to the SPARCstation 10 which runs SunOS 4.1.4.  My question of you is do V3, and V4 still work.  I've gotta serve each of these.

And thanks again for getting me started on a solution

Edit: This fix does not prevent NFSv3 and NFSv4 from working.

---

