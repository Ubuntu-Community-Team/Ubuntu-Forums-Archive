---
title: "How can I delete a program that I compiled"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-25
Here is my problem: I have installed a program on my desktop (Manual compilation) and I was wondering, if I delete the folder that is on the desktop, will I lose the program, or is it safely copied to another location, and does the same go to libraries, because I have installed a C++ library on my desktop as well. (To make it clearer, I have unzipped the tar.gz file to my desktop, and then entered the configure file from there!)

Thanks for any help in advance!

---

### Post by bodhi.zazen on 2011-08-25
depends on the program.

If the developer was kind you can simply run make uninstall

If not you will have to manually find and delete the files from your system.

Did your read the README ?

---

### Post by the-new-x on 2011-08-25
> **bodhi.zazen said:**
> depends on the program.

If the developer was kind you can simply run make uninstall

If not you will have to manually find and delete the files from your system.

Did your read the README ?
To be honest, not all of it!
But my main problem is not that I want to uninstall the program, it is that I want to delete the folder on the desktop and still be able to run the program, and if not delete, then move but without facing any problems...
And thanks for the reply!

---

### Post by FormatSeize on 2011-08-25
If by ``folder'', you mean the thing that appeared after you extracted the compressed file that you were in when you ran ./configure, make, and make install, then yes, you can delete that folder and still run the program. That's not the place where the program is installed if it's a typical program.

---

### Post by bodhi.zazen on 2011-08-25
> **the-new-x said:**
> To be honest, not all of it!
But my main problem is not that I want to uninstall the program, it is that I want to delete the folder on the desktop and still be able to run the program, and if not delete, then move but without facing any problems...
And thanks for the reply!

Yes you can delete the directory with the source code, but, IMO, unless you are somehow tight on space I suggest you keep it.

I typically keep such things in ~/src

---

### Post by the-new-x on 2011-08-25
Thanks for the help guys, really appreciate it, and if deleting them won't do any damage to the program, then copying them will not do any damage as well, so I will keep them as you suggested bodhi.zazen...

Again, thanks guys!

---

### Post by Wim Sturkenboom on 2011-08-25
Rename the folder, run the program and check if it still works. If so, it's safe to (re)move the folder (unless the program is actually in that folder).

---

### Post by the-new-x on 2011-08-25
> **Wim Sturkenboom said:**
> Rename the folder, run the program and check if it still works. If so, it's safe to (re)move the folder (unless the program is actually in that folder).
An even better solution, thanks for the help Wim!

---

