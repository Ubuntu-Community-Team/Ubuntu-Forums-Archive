---
title: "Cannot view all folders with certain computers"
date: 2015-04-11
forum: Networking &amp; Wireless
---

### Post by joerack on 2015-04-11
Hello,
I'm trying to build a nas pc with xubuntu installed.

I've shared with samba the entire home folder, so I have downloads, videos, etc, whenever the remote drive is accessed.

Problem is that I cannot play all videos from certain computers.
Eg. my main computer upstairs can access and reproduce all videos, but from downstairs I'm getting strange errors...

Help?

---

### Post by TheFu on 2015-04-12
Home directories are special to samba.  It is usually best to use the [homes] stanza to control access by the userid.  Trying to allow other users access to files under a HOME isn't a good idea.  Either, use the [homes] method built-into samba or move the files to storage outside a HOME.

However, if the intent is to share media, movies, tv, videos, music and pictures, then might I suggest Plex Server?  Plex is good if you don't need to control access to the files - it is a DLNA server, so any DLNA client on the same subnet gets access - no authentication. Of course, if you pay the Plex guys (monthly), then you can access anything over the internet with their help (or you can setup a VPN and do this yourself for free).

Assuming you still need/want to use samba, please post your smb.conf file (please use "code tags" so things line up nice too - AdvReply).  There are very good reasons to use samba for this.  Also, show the full permissions for every directory you want to share.

---

