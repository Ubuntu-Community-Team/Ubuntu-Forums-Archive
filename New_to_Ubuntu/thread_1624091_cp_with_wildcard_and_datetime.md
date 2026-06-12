---
title: "cp with wildcard and datetime"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by garymlewis on 2010-11-17
I'd like to copy all files in one directory to a second directory and append a datetime to the file name. Something like the following:

cp *.* ../archive/*.*.$(date +%Y%m%d%H%M%S)

The wildcards in the destination get translated literally, so the copied file ends with a name like *.*.20101117125353

Any ideas?

Thanks very much.
Gary

---

### Post by papibe on 2010-11-17
In order to accomplish what you want, you'll need a little bit of basic shell scripting:
```
$ for file in *; do
> copy $file ../archive/$file.$(date +%Y%m%d%H%M%S)
> done
```

I believe you're trying to do a nice organized backup of your files. It may be a good idea to look into the command rsync. Search the forums and google, there's lots of tutorials around.

Good Luck!

EDIT: the '>' prompt is automatically generated after you press enter on the first line. After you press enter on the 'done' line, the script is executed.

---

### Post by garymlewis on 2010-11-17
Thanks so much. Looks like it will work perfectly. I'll also check out rsync.

I appreciate your help.
Gary

---

