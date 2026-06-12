---
title: "Appdata folder for uTorrent (Wine)"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by GXice on 2009-09-08
Hi guys,

As you all know, uTorrent works fine under Wine. However, in Windows uTorrent has a folder in the %Appdata%\Roaming folder where uTorrent stores all the settings and resume information for torrents.

Does anyone know where this folder can be found in Ubuntu when uTorrent is installed with Wine? Thanks

---

### Post by Sinkingships7 on 2009-09-08
You should be able to find this data in your .wine folder (hidden in your Home folder). There will be subfolders representing the C drive, then program files, then utorrent, and that's where you should be able to find it.

Sorry I couldn't be more exact. I'm not on my Ubuntu machine right now.

---

### Post by GXice on 2009-09-08
> **Sinkingships7 said:**
> You should be able to find this data in your .wine folder (hidden in your Home folder). There will be subfolders representing the C drive, then program files, then utorrent, and that's where you should be able to find it.

Sorry I couldn't be more exact. I'm not on my Ubuntu machine right now.

I went there, all I could find was uTorrent.exe and a .dmp file which isn't what I'm looking for.

I'm migrating hard drives and would like to keep all my uTorrent settings and torrents as they were.

---

### Post by GXice on 2009-09-08
Found it!

Its located in: 
/home/{username}/.wine/drive_c/windows/profiles/{username}/Application Data

Should find a folder called uTorrent in there with you seek.

---

