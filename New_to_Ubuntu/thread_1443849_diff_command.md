---
title: "diff command"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Guruprasad on 2010-03-31
I have php code file in folder MAIN.
I copied the file to another folder name MODIFIED and edited few and added few new files.

Using diff command I am trying to create a patch.

If I want to have the new files also to be included in the patch then what should be the command?

---

### Post by slakkie on 2010-03-31
diff -u <new> <old> > file.patch


to apply the patch you would do:

patch < /path/to/patch.file

to reverse the patch:

patch -R < /path/to/patch.file


Have a look at man diff and man patch. Best of luck!

---

### Post by Guruprasad on 2010-03-31
Thanks

But this will output the newly created files a ONLY IN PATH-TO-MODIFIED

I would like to have the newly created files also in patch

---

### Post by slakkie on 2010-03-31
-r is recursive, so, diff -ur new_dir old_dir > patch.file

---

