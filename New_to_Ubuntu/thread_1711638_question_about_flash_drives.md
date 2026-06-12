---
title: "question about flash drives"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by jermza on 2011-03-21
Apologies if this isn't related to Ubuntu.

If I insert a flash drive into my USB port and I delete a file that's on it, I find that the file isn't actually deleted but rather moved to a folder caller ".trash100" or something.  I have to delete THAT folder in order to completely remove the file on the flash disk.

Is this an Ubuntu thing, or is it related to the flash drive itself?

---

### Post by lisati on 2011-03-21
The "Trash can" is the Ubuntu equivalent of Windows' "Recycle bin." Does emptying the trashcan from your desktop help?

---

### Post by mikechant on 2011-03-22
If you're using Nautilus to delete the file (that's the standard file manager), there is an option in 'preferences' to add a proper 'delete' command to the right-click menu. Once you've done this you can right-click on any file and select 'delete' and that will delete without using the Trash can/Recycle bin. It should work the same on Hard drives or USB drives.

---

### Post by Paqman on 2011-03-22
You can use shift-delete to delete things fully without sending them to the trash.

---

### Post by crispy_420 on 2011-03-22
Shift + Delete as mentioned just previous will solve the issue I believe. But if you are worried about recovery, FAT may not be the best file system to use. Anything you delete, especially on flash drives, may be recoverable for a very extended period. You want to make sure nobody can easy recover what you thought you deleted, encrypt the file system with something like truecrypt. That way if you close it after deleting the recycle bin is encrypted too.

Too much info?

---

