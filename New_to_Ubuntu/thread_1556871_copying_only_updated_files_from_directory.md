---
title: "copying only updated files from directory"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by imran_dindore on 2010-08-20
hay guyz is there any trick for copying only updated files from big repositories....i need to copy updates packages from my friends system...so everytime i have to copy all the repositories and paste it in my own repo, replacing same files..could anyone please suggest a way so that i would be able to only copy updated files and avoid copying all the big repository every time i need to update my synaptic package manager..
thnx in advance

---

### Post by Gone fishing on 2010-08-20
If you had you packages copied onto an external media which you could plug into both boxes you could use the cp -u switch which will:

> -u, --update
copy  only  when  the  SOURCE file is newer than the destination file or when the destination file is missing

You could use the cp -p switch to copy your repository onto the external media thus preserving ownerships time stamps etc.

have a look at man cp

---

### Post by imran_dindore on 2010-08-20
well i am a newbie brother..see the thing is all the files in that repo directory have different time stamp from 2010 mar till uptill now...so i just wanto copy file from d date lets say 2010 july ONWARDS to another directory...so can we do that by any command..

---

### Post by Gone fishing on 2010-08-21
I was thinking of you making a copy of you brothers directory on to external media, using cp -p, then using use cp -u to keep it updated and use that to update your box also using cp -u.

However, you need to make a script to do what you want, using the find command and then using the cp command. Have a look at: [http://www.unix.com/solaris/41173-copy-files-newer-than-specific-date.html](http://www.unix.com/solaris/41173-copy-files-newer-than-specific-date.html) and [http://www.linux.org/lessons/tips/cmndline.html](http://www.linux.org/lessons/tips/cmndline.html)

I think something like  

$ find /home/john -mtime -30 -exec cp -p {} /home/john/test/ \;

where -30 is files newer than 30 days old

---

