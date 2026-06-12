---
title: "create rar from selected files script"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by SushiAddiction on 2011-04-13
Unfortunately archive manager does not have 'store' and 'recovery record' option. 

I want to make a nautilus script that will create a single rar file from all selected files.(single and multiple files)

I've tried
[http://ubuntuforums.org/showthread.php?t=708398](http://ubuntuforums.org/showthread.php?t=708398)

I need the script to be able to handle spaces. I've search the forum for hours :( 

at the moment I have

```

#!/bin/bash
#
rar a -rr1% -v180m -m0 "zarchive.rar" "$*"
```My plan is to create something with zenity
1. how do I make the archive name the same as the first file selected?
2. How can I handle multiple files. eg file.mkv another.mkv > file.rar

thanks for any help

>edit This handles filenames with spaces
```

rar a -v180m -m0 "$*.rar" "$*"

```

---

### Post by hoink on 2011-04-13
I can't help you, but I did enjoy learning about Zenity.

I think this forum would be able to help you.

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by SushiAddiction on 2011-04-13
```
#!/bin/bash
#
rar a -rr1% -v180m -m0 "$1" "$*"
```This should work. It does use the first file name for the rar archive name... but it does not do multiple files.

what am i doing wrong?

EDIT>problem solved though trial and error
```

rar a -v180m -m0 -rr1% "$1.rar" "$@"

```this works as a nautilus script with multiple files to one rar file with the first file selected as the rar file name.
I've only been using linux for a month. More options = steeper learning curve :|

---

