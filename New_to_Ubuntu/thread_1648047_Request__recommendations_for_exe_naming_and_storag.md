---
title: "Request  recommendations for exe naming and storage"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by shoepiece on 2010-12-18
I would like to hear some recommendations for naming and storing custom executable files. Would it be unwise to store executables in /usr/local/bin? And how to name (.out, .exe, .bin), I know that an extension is not necessary but I prefer to have one for my own benefit. Please advise, thanks.

---

### Post by hwychld on 2010-12-18
If you are talking about scripts you have written then ~/bin is a good place to store them.  Once you create this directory it will automatically be put in the executable path.  

As for an extension I suppose you could use .sh for scripts.  They really aren't needed though.  Executable's are color coded when you get a listing via ls.

It doesn't appear to me that Nautalis indicates when a file is executable though.  You can always use the command file at the command line to determine what kind of file it is:

```

user@VBox:~/bin$ file new
new: Bourne-Again shell script text executable

```

Linux doesn't really care about file extensions so pick what you want I guess.  I might stay away from .exe since those usually indicate a windows executable.

---

