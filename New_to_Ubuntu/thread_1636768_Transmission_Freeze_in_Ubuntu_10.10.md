---
title: "Transmission Freeze in Ubuntu 10.10"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by duegogo on 2010-12-03
Hello,
So when I use transmission in 10.10, it just freezes whenever I use it.  And when I try to kill it, it won't be killed!

```

me@-Inspiron-1520:~$ pidof transmission-gt 
2316
me@-Inspiron-1520:~$ kill -9 2316
me@-Inspiron-1520:~$ pidof transmission-gt 
2316

```

So I was wondering if I can either a) get an older version that doesn't hang, or b) use an alternative BT program?

---

### Post by Zzl1xndd on 2010-12-03
transmission works well for me, but my second favorite is Deluge. 

Its available via the Software Centre.

---

### Post by duegogo on 2010-12-06
In addition, when I try to kill the process from gnome-system-monitor, I see that the transmission-gtk process, although defunct, is "uninterruptible."  It is also in waiting channel: _wait_on_freeing_inode.  Any ideas what could be wrong with my transmission?

---

### Post by Nakken on 2011-01-02
This happens to me as well if using a slow memory stick as download directory. Try limiting the speed to f.x 50kbit, does it help?

---

### Post by efini on 2011-01-27
Are you saving the torrent in an encrypted partition?

If it's a large torrent and Transmission is configured to pre-allocate space for torrents, your PC could appear to freeze because it's busy performing the encryption when the torrent starts. This will also cause connections to be dropped very shortly after the torrent starts.

Try saving the torrent to an unencrypted partition. Hope this helps you.

---

