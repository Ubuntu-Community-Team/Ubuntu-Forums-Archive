---
title: "What to do with a *.sh file?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by mmjensen on 2009-06-07
Hello
 
Just got ubuntu, after using windows for a lot of years.
I've downloaded a game, which is a *.sh file. What to do with it? How do I install it?
 
Please help.

---

### Post by jbruced on 2009-06-07
Check out here

[http://ubuntuforums.org/showthread.php?t=282827](http://ubuntuforums.org/showthread.php?t=282827)

---

### Post by mmjensen on 2009-06-07
Thanks.
But it just says:
sh: Can't open *filename*

---

### Post by munky99999 on 2009-06-07
cd to the directory the sh file is in.

> sh myfile.sh

---

### Post by mmjensen on 2009-06-07
Thanks.

Now I get this message
> /home/mads/.setup6121: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by ajgreeny on 2009-06-07
What exactly is the file supposed to be doing?  You can always open it in text editor (Gedit) to see if you can sort out the problem by looking for any files it refers to which you don't have, like the libgtk-1.2.so.0 you mention.

Just be certain you really know what you are doing with a .sh file, as it could possibly cause you problems, particularly if you allow it to do anything in the filesystem.

---

### Post by mmjensen on 2009-06-07
It's a game.
I'm not concerned, just installed ubuntu - I can always start over :)

---

### Post by niteshifter on 2009-06-07
Hi,

Open Synaptic and search for libgtk. I'm betting that libgtk2.0 is installed but libgtk1.2 isn't. You'll need both libgtk1.2 and libgtk1.2-common.

**Do not remove libgtk2.0!** Both packages can co-exist. Removal of the 2.0 version will break your system.

---

