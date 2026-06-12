---
title: "Hidden directories"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by dimothy10 on 2009-02-28
Is there a way to remove a directories hidden status?  From what i understand if you name a directory /."dir" it becomes hidden.  Is there a way to unhide it or indeed some argument that could be added to the wipe terminal command to allow it to see the directory to be wiped?

thanks

---

### Post by championboxes on 2009-02-28
Im not sure how to do it in the terminal but you should be able to go to the directory the hidden file is in and press Ctrl+H and it should show all the hidden files

---

### Post by WhiskyChris on 2009-02-28
I know that in a terminal if you type

ls -a

this lists all files in the current directory where the -a flag specifies all which includes . .. and anything prefixed with a dot.

Don't know if this helps, just my 2 cents worth (and my first post!)

---

### Post by sisco311 on 2009-02-28
```
ls -a
```
or use the tab completion
```
command .<hit-TAB-twice>
```

---

### Post by quinnten83 on 2009-02-28
couple of options here:
in a folder press ctrl+H to show hidden files
in Nautilus (the filebrowser) select edit>preferences and then select "show hidden files".
also in terminal when checking your files and folders, do a ls -a.

---

### Post by lordharsha on 2009-02-28
Everything mentioned above will work, but I got the impression that you wanted to remove the hidden status permanently. If that's the case, simply rename the file and remove the "." at the beginning of the name.

---

### Post by dimothy10 on 2009-02-28
Thanks for all the help!   Lordharsha, you were correct i was trying to remove the hidden attribute from the directory, did not think it would be that easy!!!

Thanks again

---

### Post by sahabcse on 2009-02-28
If the user has full permission in .hiddednfolder means removing dir is not a big deal.............

---

