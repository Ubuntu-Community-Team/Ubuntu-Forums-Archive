---
title: "update manager repositorys"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by tedygram311 on 2010-10-19
I have been performing system updates regularly and this popped up... should I be worried?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

also this one....

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http:
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http:

I am really just wondering what I should do to replace it with a repository that does work.

---

### Post by Sealbhach on 2010-10-19
I get the same error, I think it's just a temporary network problem. You could try going into Software Sources and doing the "select best server" thing in the "Download From" box.

---

### Post by tedygram311 on 2010-10-19
Yea still have that notice though and have had it for awhile anybody know anything about it?

---

### Post by the.phantom on 2010-10-19
gotta be some sick servers


if you UNcheck sun java you should be able to get the updates (conical partners)

been that way for about 12 hours now

once i got sun to stat the download but was at 28K so gave up after 20 min

does the same on 3 ubuntu systems i have 10.04,10.04,10.10

happens on "select best server, main server, and server for usa

---

