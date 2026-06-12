---
title: "Windows share - uploading - modified timestamp weirdness"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by darkninja on 2006-11-27
Hello, I've noticed some strange behaviours from Samba when uploading files to a remote share from a Ubuntu system. I've seen this both on Edgy and Feisty which I'm currently running under VMware.

Basically, when you upload a file to the remote Windows share the "Modified:" is changed to the current time/date. Strangely, this does not happen when downloading an existing file.

Hence if I user was trying to backup their data by uploading it to a remote share, their real modified dates will be replaced. This could be disastrous for critical documents, photos, graphics  etc...

Windows does NOT do this and I don't believe that it should be happening at all. I'd like some feedback on this and if I should file a bug report or not.

---

### Post by darkninja on 2006-11-27
OK, I've opened a bug report.

[https://launchpad.net/distros/ubuntu/+source/samba/+bug/73452](https://launchpad.net/distros/ubuntu/+source/samba/+bug/73452)

I'd still like to hear from anyone to see if it's not just me.

---

### Post by chaos_abl on 2007-05-17
Hello darkninja,

I'm just having the same problem with my samba-share on a Dapper-Drake-server. When I upload a file from my feisty desktop, the timestamp is modified (with the actual systemtime). Same procedure from a Win XP-desktop doesn't change the timestamp (also a XP installation running in VirtualbBox on my feisty desktop doesn't change the timestamp). Do you found a solution for this problem?

Thanks,
Chaos

---

