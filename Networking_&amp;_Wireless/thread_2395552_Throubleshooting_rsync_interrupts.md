---
title: "Throubleshooting rsync interrupts"
date: 2018-07-03
forum: Networking &amp; Wireless
---

### Post by AnrDaemon on 2018-07-03
I have a remote host (VPS, a webserver) to which I'm frequently syncing files (uploading new version of website from staging area).
For some time, I'm having a problem I can't diagnoze no matter what I try.
About halfway into scanning the remote directory, the session just crashes and disconnects without any messages.
If I then immediately restart the upload script, the session run to completion without any issues.
The uploaded files are small (tens of kB at most), the number of files per directory is also small (tens at most).

Local command is ```
/usr/bin/rsync -Fxtcrv --iconv="." -M--msgs2stderr --rsh="ssh" --rsync-path='$HOME/bin/rsyncd' -- "export/" "user@host::section/"
```
Remote daemon wrapper (~/bin/rsyncd) is ```
/usr/bin/rsync --config="$HOME/.rsyncd" "$@" 2> "$HOME/logs/rsync-$(date +%s).log"
```
Remote logs are all empty, no error messages, nothing.

It interrupts even if there's nothing to upload.
> […]$ deploy.sh
sending incremental file list

[…]$ deploy.sh
sending incremental file list

sent 38,255 bytes  received 137 bytes  15,356.80 bytes/sec
total size is 5,209,533  speedup is 135.69

---

