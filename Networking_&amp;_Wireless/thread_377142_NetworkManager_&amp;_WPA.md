---
title: "NetworkManager &amp; WPA"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by Veridicus on 2007-03-05
I've read that network manager will help with WPA.  I've been trying to make this work.  When I install network manager though, for one it doesn't appear in applications internet, and either it is seems to be only looking for a wired connection.  I cannot find where to connect with wireless and choose WPA.  I tried uninstalling and re-installing.  What more should I do?  Thanks in advance for the help... I know there is multiple threads on WPA and network manager already, none seem to directly address this issue though.

---

### Post by Floppyjoe on 2007-03-05
> **Veridicus said:**
> I've read that network manager will help with WPA.  I've been trying to make this work.  When I install network manager though, for one it doesn't appear in applications internet, and either it is seems to be only looking for a wired connection.  I cannot find where to connect with wireless and choose WPA.  I tried uninstalling and re-installing.  What more should I do?  Thanks in advance for the help... I know there is multiple threads on WPA and network manager already, none seem to directly address this issue though.

Network Manager will only appear as an Icon on the top panel and not in the menu system.
You need to have all your network interfaces disabled in System/Administration/Networking for Network Manager to function correctly.
Also for WPA you will need to set up the WPA config file as described in the WPAHOWTO wiki
Hope this helps.

Floppyjoe

---

### Post by Veridicus on 2007-03-05
Thanks Floppy, got it up and running now.  Didn't need to mess with the WPA config file in the end, maybe because I'm using Dapper, which I didn't specify before.  Anyway, thanks again.

---

