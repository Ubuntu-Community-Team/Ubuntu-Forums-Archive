---
title: "[SOLVED] Can't run .bin files"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by DirtyBirdNJ on 2008-12-28
Hello, for some reason I am unable to execute .bin files. I have an installer for Adobe AIR and for Google Earth that just won't do anything for me. I read that the way to execute a .bin file is just to navigate to the directory that contains it and type the filename. Whenever I do this, I get "bash: GoogleEarthLinux.bin: command not found"

I right clicked on the files and made them writable. When I did the icon changed. When I double click them, ubuntu tells me "There is no application installed for this file type".

---

### Post by DirtyBirdNJ on 2008-12-28
Found the solution!

I have to run .bin files with the sh command.

sh GoogleEarthLinux.bin worked like a charm!

[http://earth.google.com/support/bin/answer.py?answer=44713&cbid=169uy5huvg43n&src=cb&lev=topic](http://earth.google.com/support/bin/answer.py?answer=44713&cbid=169uy5huvg43n&src=cb&lev=topic)

---

### Post by HotShotDJ on 2008-12-28
If you absolutely must use *.bin files (sometimes unavoidable), you must include ./ in front of the command.

---

### Post by northern lights on 2008-12-28
```
cd /path/to/GEbinFile/
sh GoogleEarthLinux.bin
```

[http://earth.google.com/support/bin/answer.py?hl=de&answer=44713]("http://earth.google.com/support/bin/answer.py?hl=de&answer=44713")

---

### Post by inxygnuu on 2008-12-28
glad you found it (that is very helpful) just remember to mark this thread as solved!:guitar:

---

