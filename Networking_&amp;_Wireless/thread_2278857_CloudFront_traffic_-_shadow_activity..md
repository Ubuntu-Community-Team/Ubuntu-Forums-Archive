---
title: "CloudFront traffic - shadow activity."
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by mogio on 2015-05-19
At each boot, Ubuntu downloads 65 MB of data, in a silent way, from CloudFront.

Can you help me? 

Screen attached.

Thank you.

# uninstalled firefox, uninstalled chrome, removed all extensions, the download starts even if i don't runs a browser. rkhunter doesnt find anything #

---

### Post by tgalati4 on 2015-05-19
Cloudfront is a rather large hosting service, so it could be anything.  Perhaps examining the packet traffic to see what the data is.  Do you have Netflix or pandora or spotify or any other media service?

---

### Post by mogio on 2015-05-30
> **tgalati4 said:**
> Cloudfront is a rather large hosting service, so it could be anything.  Perhaps examining the packet traffic to see what the data is.  Do you have Netflix or pandora or spotify or any other media service?

It was dropbox! 60 mb of sync every boot? wtf.
Uninstalled and switched to MEGA. thanks

---

### Post by tgalati4 on 2015-05-30
How large was your dropbox data pool?  It could simply be the meta-data that is needed to determine which files need updating between boots.  It's probably normal.  If you had an empty dropbox folder, then I would be suspicious.

---

