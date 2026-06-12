---
title: "pwd: failed to stat `.': No such file or directory"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Ajay Ramaseshan on 2010-11-23
Hello I was in my command window in a particular directory
and was in the GUI also in same directory.. and from GUI i 
went to the immediate top-level directory and pressed 
shift-del for the directory in coammnd line.
After that command line started to throw up error when i executed
pwd command.
pwd: failed to stat `.': No such file or directory

Just curious to know what this error means.

---

### Post by karlwbloedorn on 2010-11-23
pwd prints out the absolute path of the directory you are currently in.

the dot represents the current directory. its similar to how ../ means the parent directory

when the pwd command attempts to use the system call stat to find out information about the specified file "." the directory is non existent. Thus resulting in error.

Here is info on stat:
[http://www.opengroup.org/onlinepubs/009695399/functions/stat.html](http://www.opengroup.org/onlinepubs/009695399/functions/stat.html)


This is the C code from the pwd command:

  if (stat (".", &dot_sb) < 0)
    error (EXIT_FAILURE, errno, _("failed to stat %s"), quote ("."));


hope this helps you understand

---

### Post by col48 on 2010-11-23
shift+del in Nautilus on the directory will have deleted the directory.  But the Terminal command line does not acknowledge this until it needs to refer to the directory (eg to create a file in it or report on it) and so it still appears to be pointing to that directory.  I observe pwd (no parameters) and pwd . both appear to report that the current directory is the one newly deleted.  But if I now do mkdir fred in the command line it reports No Such Directory - and it must be referring to the newly deleted current directory rather than fred, the one I am attempting to create.

So the Terminal does not change where its pointer to the current directory is pointing to the moment something else deletes that directory.  I guess it keeps the name in memory so does not refer to the hard drive until it needs to do some operation on/using the directory.

---

