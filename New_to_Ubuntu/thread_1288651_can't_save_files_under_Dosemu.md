---
title: "can't save files under Dosemu"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by ray field on 2009-10-11
I'm running an old DOS app under Dosemu, and I've managed to set the permissions on the partition where the files are to r/w, so far so good.  however, I'm missing something: though I can change a text file in that partition under Ubuntu using say, gedit, and then save it without problem -- when I call up a file with XyWrite, my old Dos word processing software, and then try to save it, I get "Path not found" -- which in my previous experience using Dosemu means that the file is locked read-only, which it is not.  

I have no problem creating a new file under DOSEMU/XyWrite and then saving it to the same directory.  

I have a feeling it's something obvious...

---

### Post by rCXer on 2009-10-11
I don't use dosemu often, but here are some troubleshooting questions.  Have you tried running dosemu as root?
```
sudo dosemu
```

Do you get this error when saving files with a different program. Enter...
```
edit
```
...into the dosemu prompt, type a bunch of random characters, and try saving in to the same folder?

In the bash terminal, can you paste the output of...
```
ls -l
```
...in the directory of the file you are trying to write to?

Have you tried dosbox? Someone wrote [some instructions](http://peregrineproject.com/balderdash/xyhow2.html) to install xyWrite in it.  Since the dosbox in the jaunty repositories is buggy you may need to get version 0.73 of dosbox from [getdeb](http://www.getdeb.net/app/Dosbox) or the [karmic repositories](http://packages.ubuntu.com/karmic/dosbox).

---

