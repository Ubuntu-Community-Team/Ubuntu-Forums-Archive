---
title: "Will the Trash folder empty automatically on reboot?"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by tdlucas on 2010-10-04
I cannot seem to find where to set preference so the above DOES NOT happen?

Some of my media files have inadvertently ended up in the trash and and I do not seem to be able to restore them to their previous folder. When accessing the trash folder a warning has come up saying 'are you sure you want to delete ... from the trash?' but if I click on Cancel the warning just re-appears.

I cannot close any windows but seem to be able to access system preferences and admin.

A reboot may fix but not if I lose the files which would be a disaster. I'm using 10.4 btw.

Can anyone help please?

Thanks

---

### Post by Clever_Username on 2010-10-04
I wouldn't think so. And I can't reboot at this second to check.:(
But if you want to be safe, you can copy the files in the trash from command line to somewhere safe.
The trash is located (from your home folder) in .local/share/Trash/files.
In the files directory you will find anything that's in the trash can.
Good luck

from your home directory:
cp .local/share/Trash/files/*filename* ~/Desktop

---

### Post by tdlucas on 2010-10-04
Many thanks for the advice. I'm able to access the trash folder through terminal so will copy the files somewhere safe before taking the reboot plunge. Disaster averted though :)

Cheers

---

