---
title: "Mounted drive in k3b"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by PeteZA on 2007-09-30
Hi All,

I am trying to write a dvd with files that are located on a shared folder which has been mounted from windows, but I can't see the share in k3b or GnomeBaker, I assume that this is being prevented by the OS for some reason?

any thoughts?

---

### Post by conjur3r on 2007-09-30
Have you tried looking under the /media folder?

---

### Post by PeteZA on 2007-09-30
The media folder shows the share, but that folder ie media/shared_folder is empty

---

### Post by conjur3r on 2007-09-30
That's very strange.  I have a NTFS mounted windows partition and K3B is navigating the folders and files without a problem.

Can you see the files/folders using your file browser or through the terminal?

---

### Post by PeteZA on 2007-09-30
Strange, it looks like my problem is with connecting to the windows PC thru the share. If I mount the drive, then I can access the mounted part, however, it seems that if I try to access the same shared folder via the network, ie. I look for it in places-->network, it tells me that the folder contents could not be displayed.

Odd

---

### Post by conjur3r on 2007-09-30
That sounds plausible to me.  The burning programs may not have support (maybe intentionally) for navigating unmounted network shares.  After you have mounted a share, it then makes it appear like another part of the system.

---

