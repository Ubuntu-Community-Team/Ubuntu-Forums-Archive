---
title: "Removing special characters from file names"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-11-17
Trying to move all my music onto another hard drive to do a clean install (going back to jaunty) the only hard drive ive got big enough is my ipod, which works fine except that it work accept file names or directories with any of these characters in the name ? : ; *
Im sure i can use the find command or something to find all these characters and replace them with . but i dont know the command.

So i want to search ~/Music recursivley find all instances of :;*? and remove them, whats my command? im too dumb to figure it with the 'man find'

---

### Post by KIAaze on 2009-11-17
This seems to work:
```
find ./Music/ \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \)
```

After that, you can use "rename" to rename the files.
I think there are a few renaming GUIs available too, but I don't know if they can search a directory recursively for patterns.

edit:
Renaming commands:
```
#replace "?" with ""
find ./Music/ \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) | xargs -n1 -I{} rename ? "" {}
#replace ";" with ""
find ./Music/ \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) | xargs -n1 -I{} rename \; "" {}
#replace ":" with ""
find ./Music/ \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) | xargs -n1 -I{} rename : "" {}
#replace "*" with ""
find ./Music/ \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) | xargs -n1 -I{} rename \* "" {}
```

[B]WARNING: If you have for example "a?a" and "a:a" and use all of the above commands, both files will be renamed to "aa", so one of them will be overwritten!
[/B]

Removing command:
```
find ./Music/ \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) | xargs -n1 -I{} rm -v {}

```

Found the renaming apps I was thinking about again (and more):
[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)
[http://www.krename.net/](http://www.krename.net/)
[http://thunar.xfce.org/pwiki/documentation/bulk_renamer](http://thunar.xfce.org/pwiki/documentation/bulk_renamer)
[http://linuxappfinder.com/package/mrename](http://linuxappfinder.com/package/mrename)

CLI info:
[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)
[http://www.devdaily.com/blog/post/linux-unix/find-how-multiple-search-patterns-filename-command](http://www.devdaily.com/blog/post/linux-unix/find-how-multiple-search-patterns-filename-command)
[http://www.softpanorama.org/Tools/Find/find_mini_tutorial.shtml](http://www.softpanorama.org/Tools/Find/find_mini_tutorial.shtml)

---

### Post by CaptainMark on 2009-11-17
Thanks, solved

---

### Post by berwin22 on 2010-12-23
I've looked around a lot for a tool that will do this, and found a few scripts, but nothing that would do exactly what I wanted.
-Rename Directories and files
-Output renames
-Go recursively down a directory
-If a file already exists by that name, append a number.

After a bit I got frustrated, and wrote my own.
[http://code.google.com/p/archivematica/source/browse/trunk/src/sanitizeNames/lib/sanitizeNames.py?](http://code.google.com/p/archivematica/source/browse/trunk/src/sanitizeNames/lib/sanitizeNames.py?)

I hope someone else finds this useful.
My co-worker should be making this into a package soonish.

Other name for this is Name sanitization/sanitse filenames.

---

