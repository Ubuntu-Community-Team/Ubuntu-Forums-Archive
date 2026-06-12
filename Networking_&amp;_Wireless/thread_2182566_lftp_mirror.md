---
title: "lftp mirror"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by AshPat on 2013-10-21
I had a question about lftp mirror command.
There is an option in it "--delete-first delete old files before transferring new ones"

This option is there as if the default cause is to not delete files before transferring new ones, but in using the lftp mirror command, when there is an updated file to be sent, the old file is always deleted first and then new one is transferred.

Has anyone been able to send files using mirror function lftp with keeping the old file until the new one has been transferred?

---

### Post by Lars Noodén on 2013-10-22
I would use rsync instead.  It's quite polished and can do deleting:

[indent]
            --del                   an alias for --delete-during
            --delete                delete extraneous files from dest dirs
            --delete-before         receiver deletes before xfer, not during
            --delete-during         receiver deletes during the transfer
            --delete-delay          find deletions during, delete after
            --delete-after          receiver deletes after transfer, not during
            --delete-excluded       also delete excluded files from dest dirs
[/indent]

rsync works over SSH now by default.  lftp seems to support SFTP but that may have to be specificed explicitly.

---

