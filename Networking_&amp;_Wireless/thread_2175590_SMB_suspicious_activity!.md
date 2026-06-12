---
title: "SMB suspicious activity!"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by jordan-mccrone on 2013-09-19
I'm seeing way too much SMB traffic over my network when computers are idle. This traffic happens between my Desktop and HTPC (both running 12.04 LTS). I ran a tcpdump and opened it in wireshark and here's one of MANY MANY packets after tcpdumping and opening in wireshark: [http://pastebin.com/CHDJYgWK](http://pastebin.com/CHDJYgWK)

Throughput averages about 200 KB/s on BOTH tx and rx simultaneously

If you look at the pastebin, it looks like one machine is scanning files on the other or something weird like that. The strange thing is I don't have ANY of the files/folders (e.g. /usr/java/*) as active shares.

What's going on?

---

### Post by tgalati4 on 2013-09-20
If you have the share in your /etc/fstab, it's possible that it is being indexed by whatever tracker you have installed.  If you are running mythTV on your HTPC, then there will be indexing for your multimedia database.  Do you have *tracker* installed?

```
apt-cache policy tracker
```

---

### Post by jordan-mccrone on 2013-09-20
My desktop does have the media directory of the htpc in fstab. However, the pastebin I posted seems to reference files on my desktop that haven't been actively mounted (at least by me or fstab) by my htpc. 

Also, I don't believe tracker is installed on either computer (both give "Installed: (none)")

---

