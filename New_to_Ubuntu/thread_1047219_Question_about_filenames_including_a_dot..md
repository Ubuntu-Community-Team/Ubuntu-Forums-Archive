---
title: "Question about filenames including a dot."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by t4ggs on 2009-01-22
When I name a file ".filename" it becomes hidden, and when i name a file "filename.whatever"  everything after the dot becomes hidden right??

so how could it be that linux understand the difference between file.mp3 and file.avi or file.odf??

---

### Post by hyper_ch on 2009-01-22
no, only when the filename starts with a dot it becomes hidden.

---

### Post by mcduck on 2009-01-22
no, only files and directories that have name *starting* with a dot are hidden.

Linux doesn't hide file name extensions, although it doesn't need them either. It simply checks the beginning of the file itself and then determines what kind of file it is.

[http://en.wikipedia.org/wiki/Magic_number_(programming)#Magic_numbers_in_files]("http://en.wikipedia.org/wiki/Magic_number_(programming)#Magic_numbers_in_files")

You can try this if you want, remove the extension from some file and then run "file *nameofyourfile*", you should get information about what type of file it is.

(Windows uses file name extensions to detect file types, as did DOS before.. Sadly, Windows also by default hides these extensions. It just does it badly, only hiding one extension while it's actually possible to have many of them.. This has resulted in pretty easy way to create trojans; just create a nasty program and rename it to something like "holidaypicture.jpg.exe". Windows will hide the .exe part and only shows "holidaypicture.jpg", and now the user will believe it's just a harmless picture..)

---

### Post by t4ggs on 2009-01-22
i see, and thanks u for the link too, it was usefull...

---

