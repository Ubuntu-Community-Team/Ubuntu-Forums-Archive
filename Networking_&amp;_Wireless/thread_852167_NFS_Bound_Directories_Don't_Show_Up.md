---
title: "NFS: Bound Directories Don't Show Up"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by lightnb on 2008-07-07
On the NFS host I have a drive mounted with:

```

/dev/sda1 /mus auto rw,users,auto,gid=1000,uid=1000,exec 0 3

```

and then a folder of that mount bound to my home folder:

```

/mus/AUDIO    /home/user/Audio   none    bind  0  0

```

I have /home/user shared with NFS. When I mount the share on the NFS client, the "Audio" folder shows up, but contains no files. How do I make the bound directories share too?

---

