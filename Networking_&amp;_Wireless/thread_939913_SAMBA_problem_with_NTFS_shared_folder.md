---
title: "SAMBA problem with NTFS shared folder"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by Shlompy on 2008-10-06
Hi everyone!
I've managed to share an NTFS folder on my Ubuntu Hardy machine with no issues.
I can access the folder from my other XP machine wirelessly.
**[SIZE="4"]BUT[/SIZE]**
when I reboot my Ubuntu machine, and logged back, the NTFS shared folder is reset, and I need to share it from the beggining. I assume this is happening because the samba service starts before ubuntu mounts my NTFS drive and thus it cannot share the NTFS folder at logon because it isn't recognise the NTFS volume.

Can someone help me here??
Is there anyway to mount the NTFS volume before samba start???

---

