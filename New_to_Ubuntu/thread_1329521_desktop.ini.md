---
title: "desktop.ini"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-11-17
Im a bit fussy about my music file and want to get rid of the files in there called desktop.ini and thumbs.db  Only thing is i dont know what they do, i googled them and could only find stuff windows related. Does ubuntu use them, should i get rid of them or leave them?

---

### Post by emigrant on 2009-11-17
Of course u can delete them. They are windows stuff.

---

### Post by NightwishFan on 2009-11-17
I think you can safely delete them. They are likely just leftovers from Windows explorer's folder and thumbnail database, which will fix itself if you ever browse the folders with Windows again.

---

### Post by pvroon on 2009-11-17
Try this:

find /home/directory -name 'desktop.ini' -exec rm -rf {} \;

and

find /home/directory -name 'thumbs.db' -exec rm -rf {} \;

Be aware that this deletes the file in between the quote from the directory you specify downwards without acknowledgement. So, use with care.

Good luck....

---

### Post by CaptainMark on 2009-11-17
im familiar with the find command, thanks for your help anyway, ill get shot of them then, any possible evidence that relates me back to windows is a bad thing.

---

