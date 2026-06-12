---
title: "Cant update/upgrade to 10.10"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Dooobz on 2010-12-10
Hello all, :D
Well, admittedly Im quite stumped on this, probably because Im quite the green horn to linux, but Ive checked a host of forums, self help sites, to no avail. They had solutions, but none of them did the trick sadly.

Was using Win7, bout 2 weeks ago when it suddenly died on me for the 5th time (4th hard drive, 5th time os went kapoot). So a good mate of mine recommended putting ubuntu on it, as he had a copy of it lying around (what version though, Im not sure, I believe it was 9.10, but I cant be sure). I was relieved to find I didnt have to get another hard drive, however, I cant seem to update anything. Video drivers, installs, upgrade to 10.10, nothing works, I get this same error message every time, and its always 65% when it fails.

(Reading database ... 65%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `tk8.4': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

Ive tried reinstalling ubuntu off a disc (tried multiple different discs in fact) but tells me they are invalid, and wont recognize them upon boot (booting as normal.) One disc contains netbook version, other desktop.
Ive tried the thumb stick method and using an external hdd, but same result as above.

Any help is appreciated, I probably just dun goofed somehow, Oh and machine specs might be helpful, not sure.
Mx15 alienware Laptop, 4 gigs ddr3, 320g wd internal hdd, Intel i3 at 2.13ghz quadcore, Nvidia 240m 512mb dedicated memory.

Thanks in advance, loving ubuntu thus far, Quite refreshing from windows.

Edit
Heres the other error message it throws with update manager. I also only offers a partial upgrade, that reverts to the previous error message (unrecoverable fatal error)

GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cariboo on 2010-12-10
The easiest way to solve your problem would be to go into System->Administration->Software Sources, and disable the CD-Rom and extras repositories.

See the screenshots, I'm using a newer version, but the principle is the same.

---

### Post by Dooobz on 2010-12-10
Thanks for the reply mate, and for the screenshots. Sadly It didnt hit the fix, but after scanning the hard drive, I think I found out what the problem is. There are two corrupted sectors, might have some sort of influence :( ID 5 has 2 bad sectors, and 197 has 5.

---

