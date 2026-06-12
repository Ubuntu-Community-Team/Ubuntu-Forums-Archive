---
title: "Groups and write permissions in netatalk"
date: 2017-06-15
forum: Networking &amp; Wireless
---

### Post by bbruecker on 2017-06-15
Hi,

I want to setup a shared folder for me and my girlfriend on my home server (ubuntu). I'm on Linux, she is using MacOS. Unfortunately NFS is not working properly on MacOS (e.G. german "umlaute", like special characts like ÜÄÖ make trouble). And after tests I found out for Linux clients NFS seems to be the fastest choice, but AFP seems to be the fastest choice for MacOS clients. My tests also made clear, that samba is the slowest -- either for Linux, or MacOS clients. We are dealing with large files, for video editing and quite large images.

So I want to set up shares for AFP and NFS.

We are dealing with different users accounts for my girlfriend and me. Accounts are set up on the linux server, MacOS and Linux clients.

I managed NFS to create folders and files with write permissions for the group "users". But I do not understand how to configure netatalk to do this. The files created via AFP always have read, write and execute permissions for user, groups and others. And the group is always my girlfriends user group. But for write permissions I need the netatalk to create folders and files with ownership of the group "users".

In short:
How can I manage netatalk to create files and folders with ownership of group "users" and write permissions for that group?

Any ideas?

---

