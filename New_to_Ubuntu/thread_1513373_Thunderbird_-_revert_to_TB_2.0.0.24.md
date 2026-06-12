---
title: "Thunderbird - revert to TB 2.0.0.24?"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by runbei on 2010-06-19
I'm finding Thunderbird 3.x really buggy. I'd like to revert to 2.0.0.24. I downloaded the .tgz file for 2.0.0.24 and extracted it to its own folder under ~/home.

Now, when I go into the folder where the files were extracted and try to do ./configure, I get an error message:

    > bash: ./configure: No such file or directory

The ls- l command didn't find a configure file, and make returns:

    > make: *** No targets specified and no makefile found.  Stop.

Searched Mozillazine and Mint forums but haven't found instructions for installing TB from a tgz file. 

Is it one of those apps you just move to the home folder and there you go? Except I tried running the thunderbird executable and a .sh file in the thunderbird folder and nothing happens. ?

---

### Post by cariboo on 2010-06-19
THere should be an install script of some sort included in the tgz file, did you try:

```
sudo ./mozilla-installer-bin
```

when you are in the Thunderbird directory?

---

### Post by runbei on 2010-06-21
Thanks. Yes, there is a mozilla-installer-bin file, but when I try to run the command there's an error:

```
./mozilla-installer-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

---

