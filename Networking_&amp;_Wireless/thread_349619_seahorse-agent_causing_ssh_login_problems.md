---
title: "seahorse-agent causing ssh login problems"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by malcomm77 on 2007-01-30
I recently added:

[INDENT]/usr/bin/seahorse-agent[/INDENT]

to my startup (session). I was trying to solve this problem:

  [INDENT][http://lists.alioth.debian.org/pipermail/pkg-evolution-maintainers/2005-August/000045.html](http://lists.alioth.debian.org/pipermail/pkg-evolution-maintainers/2005-August/000045.html)[/INDENT]

Running seahorse-agent fixed that problem, but it seems to have caused a problem with ssh. After running the seahorse-agent I could not login to any remote machine. I do use ssh keys, so I assume that this is the reason seahorse is getting involved. After killing the seahorse-agent I can ssh to machine without issue.

When I try to ssh, it just hangs. No error messages. I put wireshark on this and it seemed to do the key exchange and get to this point:

[INDENT]No.     Time        Source                Destination           Protocol Info[/INDENT]
[INDENT]     87 33.847567   172.31.252.212        172.31.252.234        TCP      52305 > ssh [ACK] Seq=984 Ack=1666 Win=10096 Len=0 TSV=145235 TSER=492922744 [/INDENT]

But nothing after that ... any help?

Env:
Edgy (with all the latest updates)
Linux mymachinename 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux

Thanks!

---

### Post by malcomm77 on 2007-02-09
I think I have found a work-around to this problem: in seahorse's gui I had to:

1) Right Click on my ssh key
2) select "Set up Computer for Secure Shell"
3) put in a valid host and username

After I did this, my life was a lot better. I'm not really sure why this needs to happen, because after I add the first host all other hosts that have a shared SSH key works perfectly. Sounds like a bug in seahorse.

--
Marcus

---

