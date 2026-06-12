---
title: "Extremly slow SFTP file transfer (no CPU usage)"
date: 2015-06-11
forum: Networking &amp; Wireless
---

### Post by uamillioner on 2015-06-11
Hi All,

Please help to solve a problem with Extremly slow SFTP file transfer. There are no problem with connection speed, it's fine, but file transfer is only 10 kB/s (no matter LAN, Internet or even VirtualBox Guest OS). Are there any parameter slowing file transfer? CPU usege lower than 1%.

Thanks!

---

### Post by TheFu on 2015-06-11
There are many options for sftp. The best place to check those out is in the manpage.  Which sftp server is being used?

For example, could a setting be inside a config file or on the server-side to limit the bandwidth?
Have you tried different cyphers?
What about increasing the log levels on both the client and server sides?

Another option is to use **scp** or **rsync**. I don't use sftp much besides a trivial 1 or 2 file transfer to show off sftp to people using filezilla or some other GUI tool. Normally, I use rsync.
```

OPTS="-av --stats --progress --delete-before "
SSH_OPTS="-T -c arcfour -o Compression=no -x"
rsync $OPTS -e "ssh $SSH_OPTS "  SRC TARGET
```
is what I use inside the LAN (never over the internet) to mirror large files.

rsync has extra options to show how things are going - like transfer speed, as you can see above.

Of course, none of this helps if you must use sftp. It does support alternate cyphers and tweaking the buffer size might help. I don't know myself.

Oh ... and with virtualbox, which sort of networking is setup, which NIC is being emulated, what is the hostOS and what is the real, physical, NIC?

---

