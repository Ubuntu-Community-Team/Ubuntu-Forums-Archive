---
title: "How to back up /etc/ppp/peers/dsl-provider"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by isee on 2011-01-08
Hi all!
Im trying to run
```
sudo pppoeconf
```
using this documentation [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

It advises I make a backup of /etc/ppp/peers/dsl-provider.  I can access it using Nautilus, but I can't put a copy of it in any of my own folders, I get:

> Error while copying.

The file "dsl-provider" cannot be handled becuse you do not have permissions to read it.

Is it good enough to put a copy of it on the Desktop in Nautilus as a backup?

Could I copy it to my own files or an external media somehow?

Cheers!

---

### Post by mikewhatever on 2011-01-08
Try opening the file with Gedit, then use 'File->Save as' (ctrl+shift+s) to save a copy to your home folder. If that doesn't work, use a Terminal window:
```
sudo cp /etc/ppp/peers/dsl-provider ~/Desktop
```

---

### Post by isee on 2011-01-08
Thanks Mikewhatever!

> Try opening the file with Gedit, then use 'File->Save as' (ctrl+shift+s) to save a copy to your home folder.

I can only access the /peers folder contents using Nautilus, so I had to open the dsl-provider file with Gedit while in Nautilus, and then I copied the contents, closed Gedit and opened it again from my panel launcher and pasted the contents into this new file, so I did get a copy of the contents onto my own desktop that way, the file name here being irrelevant for now.


> If that doesn't work, use a Terminal window:
Code:
sudo cp /etc/ppp/peers/dsl-provider ~/Desktop

This moved a locked root copy to my Desktop, which is fine I guess, as long as I can put it back properly if I have to.

Thanks Again!

---

### Post by mikewhatever on 2011-01-08
Welcome, and to put the file back into /etc/ppp/peers/, use the following command:
```
sudo cp ~/Desktop/dsl-provider /etc/ppp/peers/
```

---

