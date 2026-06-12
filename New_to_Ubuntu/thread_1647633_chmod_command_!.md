---
title: "chmod command ?!"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by theluli on 2010-12-17
Hi

l need advise , l am trying to use chmod command but is not working 
anyone knows why why ?

---

### Post by CharlesA on 2010-12-17
We'd need more information.

What is the exact command you are using and what does it say after you run it?

---

### Post by hwychld on 2010-12-17
I assume you are trying to change the permissions on a folder or file.  Since this is the beginner forum lets do it from the GUI first:

Places->Home Folder 

to open Nautilus in your home directory.  Browse to the file you want to change permissions.  Select it and right click and pick properties.  The third tab will be permissions.  Click away to set them the way you want.

Now to answer your question about chmod.

```

user@home:~$ chmod 755 filename

```

This will assign the owner read, write, execute permissions, the group read and execute, and others read and execute.  You can also use the following style syntax as well

```

user@home:~$ chmod +x filename

```

Which will make the file executable by everybody.  Likely reasons for failure are lack of permissions to modify the file in question.  So you would have to do something like this:

```

user@home:~$ sudo chmod +x filename

```

And enter your sudo password when prompted.  Finally, for more info

```

user@home:~$ man chmod

```

Hope this helps.  If not, post the error you receive.

---

