---
title: "recently reinstalled ubuntu"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-02-13
Now when i got to <Places <Computer <File System I have a directory called lost + found.  Just wondering what this directory is used for?

---

### Post by drs305 on 2009-02-13
The "lost+found" folder is created when an fsck check is accomplished. The system creates the folder so fsck can place corrupted files within the folder and you can inspect them before deleting them from your machine.

If you delete the folder it will reappear the next time fsck is run.

---

### Post by S0m3th1ngw13rd on 2009-02-13
ok so Ill just leave it alone. Thank you

---

### Post by drs305 on 2009-02-13
If seeing it bothers you, in the same directory you can create a file named ".hidden". Open it for editing with any text editor. Any file you list within .hidden will not be displayed in nautilus if you have your preferences set to not display hidden files.

So edit .hidden and on the first line type "lost+found" without the quotes. You can also hide any other folders/files you want. 

Save the file and set your nautilus preferences to hide hidden files (CTRL-H). You won't see any files listed in .hidden within the file browser. You will still see them via command line inputs.

---

