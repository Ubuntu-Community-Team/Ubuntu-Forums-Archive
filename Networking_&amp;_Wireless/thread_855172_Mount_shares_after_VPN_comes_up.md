---
title: "Mount shares after VPN comes up"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by rarr on 2008-07-10
I need to auto mount shares after a VPN connection is active.

I'm using the gnome network manager to establish the VPN but I can't find a way to get the shares to auto mount.

I've been down the route of /etc/networks/interface but I'm lead to believe that the gnome network administrator tool doesn't use this. [Source]("http://www.mail-archive.com/networkmanager-list@gnome.org/msg07570.html")

How can I get the gnome network manager to do this?  Bearing in mind I'm going to be supplying this laptop to people that want to click one button and be connected to the VPN with all shares active.

Cheers.

---

### Post by rarr on 2008-07-16
No one able to give anypointers?  I'm still scratching my head :-/

---

### Post by RMOP on 2008-11-14
This link relevant?

[http://thatsquality.com/linux/mounting-windows-smb-file-shares-using-cifs](http://thatsquality.com/linux/mounting-windows-smb-file-shares-using-cifs)

Worked great for me when on my LOCAL network, but failed over my VPN when away. I suspect this faiure may be because the auto-mount configuration does its stuff before the VPN can be established.

Might there be a way to force the system to re-mount using the same info after the VPN is up? I'd like to think so, and maybe it's easier than I realize, as I'm pointing to the same (internal) IP address over both the local net and when connected by VPN.

Hope this may provide a lead. Please let me know.

> **rarr said:**
> No one able to give anypointers?  I'm still scratching my head :-/

---

### Post by RMOP on 2008-11-14
Don't know if Nautilus bookmarks (Places->Connect to Server) to your shares would work or not, as I've no idea if such could be distributed to other users. I just tried it on my machine, and it does provide a persistent, one-click approach. I've an issue making the mounted share show up where I want it instead of on the desktop, but otherwise it works.

> **rarr said:**
> No one able to give anypointers?  I'm still scratching my head :-/

---

