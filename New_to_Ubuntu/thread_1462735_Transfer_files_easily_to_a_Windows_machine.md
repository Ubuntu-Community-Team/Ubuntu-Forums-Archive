---
title: "Transfer files easily to a Windows machine"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by rkakkar on 2010-04-26
I have Kubuntu installed and its connected on a LAN network to a windows machine. I want to easily transfer files to & fro the Windows machine. Something like I drop the file in a "box" on kubuntu and then pick it out on the windows machine. What's the best way to do this?

---

### Post by marshmallow1304 on 2010-04-26
[Giver]("apt://giver") will do this.  It works great on Linux and there is [an unofficial Windows version]("http://ankitjain.org/blog/giver-on-windows/").  You could also just set up samba on the Ubuntu machine (right-click->Sharing options) and mount the shares in Windows.  There are probably other options as well.

---

### Post by rkakkar on 2010-04-26
> **marshmallow1304 said:**
> [Giver]("apt://giver") will do this.  It works great on Linux and there is [an unofficial Windows version]("http://ankitjain.org/blog/giver-on-windows/").  You could also just set up samba on the Ubuntu machine (right-click->Sharing options) and mount the shares in Windows.  There are probably other options as well.

For some reason, Giver wasn't able to detect the other machine on either machine. So instead I took the Samba route and mounted a folder as my dropbox.

---

