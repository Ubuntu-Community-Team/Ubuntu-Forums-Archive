---
title: "Open office writer giving me issues"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by PwnCakes193 on 2009-02-22
I just installed OpenOffice 3.0.1 and everything works perfectly except for Writer. i keep on getting this error
Due to an unexepcted error, openoffice.org crashed. all the files you were woring on will now be saved. the next time openoffice.org is launched, your files will be recovered automatically.
The following files will be recovered:


this keeps on happening, how do i fix it?

---

### Post by Furry_Fighter_20x66 on 2009-02-22
I had this happen to me when the preference files in the home directory became corrupt somehow. Rename the .openoffice.org file in your home directory and reboot (to ensure no hanged instances of openoffice are running in the background) then try to launch open office again. You will have to press Ctrl-H in the file browser window to display hidden files so you can see it and rename it. If you need me to elaborate any more just ask.

Hope this helps.

---

### Post by PwnCakes193 on 2009-02-22
> **Furry_Fighter_20x66 said:**
> I had this happen to me when the preference files in the home directory became corrupt somehow. Rename the .openoffice.org file in your home directory and reboot (to ensure no hanged instances of openoffice are running in the background) then try to launch open office again. You will have to press Ctrl-H in the file browser window to display hidden files so you can see it and rename it. If you need me to elaborate any more just ask.

Hope this helps.

What do I rename it to?
Also, do I rename the folder or is there something else that I should fix?

---

### Post by llamabr on 2009-02-22
You can rename it to anything, as it will create a new one when you restart.

You don't need to reboot.  You can manually kill anything that's running by looking in top, or ps aux.

If it works, you can just rm the one you renamed.

---

### Post by PwnCakes193 on 2009-02-22
> **llamabr said:**
> You can rename it to anything, as it will create a new one when you restart.

You don't need to reboot.  You can manually kill anything that's running by looking in top, or ps aux.

If it works, you can just rm the one you renamed.


i love you. haha. This work needs to be done, and I need to do it before school tomorrow. Thanks a hell of a lot. Both of you guys.

---

