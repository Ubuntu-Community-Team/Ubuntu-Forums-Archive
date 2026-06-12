---
title: "nfs/autofs and symbolic links"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by skiani on 2007-07-28
Hi, I'm trying to set up a laptop as an autofs (NFS) client to my network here such that I can switch from wired to wireless and have symbolic links work/not hang. My configuration on the client is to use auto.net to mount my network server (which works great). I have symbolic links in my home directory to some folders on the server. Disconnecting from my wired network causes anything that is pointing to those symbolic links to hang indefinitely. I find that I can't even shutdown the computer unless I reconnect the wired network. I would like to be able to work in all three modes wired/wireless/completely-disconnected but don't appear to be able to do that. Note also my log shows lots of "nfs: server server not responding, still trying". There must be a time out for this stuff, any suggestions? Thanks,

---

