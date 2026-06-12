---
title: "Remote Home and Wireless"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by GaryParr on 2008-09-04
Hello all,

Had a recent laptop disaster and lost my drive. I would like to setup my new laptop (shared with my wife) so that /home is located on a separate PC with a nice big RAID array.

My problem is that the laptop lives off wireless and, well... I'm not sure if it is possible to get a wireless connection prior to logging on which would mean no remote /home mount.

Any thoughts on this would be greatly appreciated.

---

### Post by Menschenfresser on 2008-09-04
I guess you could remotely mount some sub folder instead? I have no experience with this, but I'm very interested in how to "correctly" do this! :-)

---

### Post by HermanAB on 2008-09-04
Use NFS to mount a distant share.  NFS is very easy to use and configure - a one liner in /etc/export and /etc/fstab.  Some googling will find examples.

Cheers,

Herman

---

### Post by GaryParr on 2008-09-04
I've looked at NFS, but doesn't the problem of the wireless connection prevent this? To my knowledge, the wireless connection is not established until *after* you log in...

---

### Post by GaryParr on 2008-09-04
Ok... I'm not thinking clearly today apparently.

If setup the wireless with a manual configuration (not roaming) then (I'm assuming) that will provide connections after boot, without having to log in... correct?

---

