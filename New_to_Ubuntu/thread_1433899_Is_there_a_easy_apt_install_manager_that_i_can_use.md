---
title: "Is there a easy apt install manager that i can use to install different file types"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by yahmorah25 on 2010-03-19
ok i have ubuntu 9.10 and it installs .deb file good but i need some thing that can install tar.gz tar.bz and other file types easyer i mean is there one that install all of them or do i got to manually install them to have that?

---

### Post by chaanakya_chiraag on 2010-03-19
You could create a script that you could then run.  If you need help, just ask :)
- Chiraag

---

### Post by n0dix on 2010-03-19
You can create a script for that. It's useful the script to descompress tar files, unp.
unp: sudo apt-get install unp.
Then unp file.tar.{bz,gz,etc...}
This is only the first step.

---

### Post by srs5694 on 2010-03-19
I wouldn't recommend using a script to automatically install tarballs (files with names ending in .tar, .tgz, .tar.gz, .tbz, .tar.bz2, or similar extensions). The reason is that there's no way of knowing what's in them or where they're supposed to be located until you uncompress them. Tarballs could include binary executables for your own architecture, binary executables for another architecture, scripts, source code, font files, digital photos, the text to the Great American Novel, a backup of an entire Linux (or non-Linux) system, etc. Any of these things could be intended to be extracted in a user's home directory, in the system root directory, or in a subdirectory of the user's choosing. I find it hard to imagine a script that would be smart enough to figure out what the tarball contains and where it should be extracted. That's the sort of task that's best left to human intelligence.

If you're not entirely sure what to do with a specific tarball, a good first step is to use the -t command to tar, as in "tar -tvzf foo.tar.gz" to see what files are present in foo.tar.gz. With any luck that'll help you identify what the tarball contains and what to do with it. If you're still in doubt, create a subdirectory, cd into it, and extract the tarball using the -x command, as in "tar -xvzf foo.tar.gz". You can then examine the files in more detail, read any README file, etc.

---

### Post by chaanakya_chiraag on 2010-03-19
What I was saying is that the OP could set up a script to install source tar.gz's and run the script with an argument to the source tar.gz.  That would make it much easier for the OP, as most installations are simply ```
./configure
make
sudo make install
```
(assuming, of course, that all dependencies are satisfied).  That's all I was talking about, not some generic script that runs through all directories, finds all tarballs, and automatically tries to install them :D

---

### Post by srs5694 on 2010-03-19
A script to automatically untar, compile, and install a source tarball is certainly more doable than one that handles all tarballs; however, yahmorah25 didn't specify a source tarball. Maybe that's what he meant, but maybe not. Also, not all source tarballs are configured and installed in the same way. Some lack a configure script, or use "make config" instead; some put source code (and associated configure scripts, Makefiles, etc.) in subdirectories rather than in the main tarball directory; some don't have a "make install" target; and so on. The way I see it, a script to handle even just source tarballs will either have to accept that it won't be able to handle a significant fraction of source tarballs or it will become very big very fast in order to deal with all the conditions. IMHO, it's better to have the user/administrator read the README file to learn how to do it.

---

