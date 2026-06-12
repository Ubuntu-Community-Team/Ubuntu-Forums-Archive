---
title: "Shared Folders Won't Let Me Write"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by rizlmilk on 2008-05-20
I have my laptop connected to an old 500 mhz desktop. My plan was to store my Music on the Desktop just for the hell of it and the learning experience. Whenever I try to add files, create a folder, or add anything to to desktop from the laptop, I get this message:

[I]Error while creating directory untitled folder.

There was an error creating the directory in smb://ubuntu/ryan/Desktop/Music.

Show More Details:
Read-only file system[/I]

I guess it thinks it's a read-only folder, but I have set all of the folders on the desktop to read and write. I don't know why it isn't letting me add or delete files from the laptop.

Any help would be appreciated, this is really frustrating.

---

### Post by helgman on 2008-05-20
> **rizlmilk said:**
> I guess it thinks it's a read-only folder, but I have set all of the folders on the desktop to read and write. I don't know why it isn't letting me add or delete files from the laptop.

I'm not doing any sharing myself but have you made the shares are read/write? I've seen this a lot with Windows-users where the shares are not read/write (not sure but I'd guess Ubuntu would have a similar feature). [Here is some documentation](https://help.ubuntu.com/8.04/internet/C/networking-shares.html).

Regards,
Helgman

---

### Post by rizlmilk on 2008-05-20
I edited to permissions by right clicking and choosing "Properties". Do I need to change them through the "Sharing Options" option when I right click?

---

### Post by helgman on 2008-05-20
There should be someone with shared folders around to answer this but if you've just changed the permissions on the "local" folder then yes, you have to change it somewhere relating to the "shared" folder since these are different sets of permissions.

Regards,
Helgman

---

### Post by dmizer on 2008-05-20
the only way i know how to resolve this is to manually mount the share via /etc/fstab with cifs as outlined in the "mount windows/samba shares" howto linked in my sig.

if you are not successful, please post in the howto, and i will do what i can to help you.

---

