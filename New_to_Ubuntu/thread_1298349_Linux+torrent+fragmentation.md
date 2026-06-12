---
title: "Linux+torrent+fragmentation"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by davesbrain on 2009-10-22
I'm sure this topic has been driven into the ground, but I was wondering about the effects of frequent torrenting would have on Linux Ubuntu (EXT3)?

I know it doesn't frag or doesn't matter on this file system, but what about large torrented files such as movies?   I download to a temp download directory in my home directory, then use convertx through wine to decompress the movie with my second physical drive as the destination for the VOB files.(The second physical drive is still NTFS), then I use NeroLinux3 to burn the compilation to disc.  Should my second hard drive be ext3 as well?

---

### Post by lovinglinux on 2009-10-22
Depending on the BitTorrent client you use, the space required for the entire download is fully allocated prior to the download, so fragmentation is not an issue. For instance, Deluge also offers a method of compact allocation, but it only works on Windows.

In regard to file conversions, I guess fragmentation is also not an issue, unless you are low on disk space.

Nevertheless, if you are not running a Windows OS on the NTFS drive, then I would recommend formatting it as ext4, which is faster than ext3.

---

