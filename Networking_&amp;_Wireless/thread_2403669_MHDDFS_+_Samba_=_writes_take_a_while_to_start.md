---
title: "MHDDFS + Samba = writes take a while to start"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by amorpheus on 2018-10-14
Hello, I'm trying to diagnose a weird issue. I have several harddrives mounted over MHDDFS, and am sharing them individually (symbolic links in a directory that's shared) as well as in the  combined pool.

Most things work fine over the network - writing and reading from the individual drives, and reading from the pool as well. However, writing to the pool has a weird issue: the larger the file, the longer transfers take to start, and they're not writing consistently once they've started, either. Files up to a few MB will insta-transfer, even a few dozen MB go quickly. But anything above takes at least some seconds to start the transfer, and with 1GB+ I'm waiting a while. (Addendum: writing to the pool locally seems to be fine and starts instantly. It's going through Samba and the network that's causing the issue.)

Samba's logs haven't been helpful, but I found out  what mhddfs is doing while I'm waiting:
mhddfs [2018-10-15 01:03:37]: [140267440191232] mhdd_getxattr: path = /mnt/hd1/File-to-Copy.mkv name = security.capability bufsize = 0
This repeats many times, thousands if not more, before the file transfer starts.

However, I have no idea what it means. Anyone?

---

### Post by amorpheus on 2018-10-15
After more research, it seems like it hangs trying to get the "[COLOR=#000000]security.capability"[/COLOR] extended attribute - for the file it's supposed to write? Trying to figure out if I can mount the MHDDFS FUSE filesystem without support for extended attributes was unsuccessful, went down too many cryptic rabbit holes to keep a clear head. Any suggestions for diagnosing this?

More Information:
[LIST]
[*]All the drives are formatted as BTRFS, with a single partition on each. Not combined or anything.
[*]After fiddling around with my network mounts on my Windows client, the same issue started happening with the direct Samba share, but was fixed quickly by setting the network drive up again. Haven't been able to reproduce it.
[*][COLOR=#d3d3d3]Reverting any customizations in Samba didn't change anything.[/COLOR]
[*]I've also tested that this happens on both Windows 7 and 10 clients. It *doesn't *happen on a Ubuntu client.
[*]It also happens copying from the command line in Windows.
[/LIST]

**I think I've narrowed it down to "strict allocate = yes" in Samba options, which I added while optimizing transfer speed. **Seems to work as expected now.

---

