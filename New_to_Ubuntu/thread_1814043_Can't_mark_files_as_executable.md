---
title: "Can't mark files as executable"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by ProfessorUnicorn on 2011-07-28
Whenever I want to run .exe files for Wine, or .java files, I get this error: "The file BLA BLA BLA is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run."

I right-click the file and go to permissions, but the check-box to mark as executable is not even there. What can I do to fix this? Also it would be nice to automatically make the files marked as executable, if possible. Thanks! 

(Also, I DO have Java installed for the .java files.)

---

### Post by lmarmisa on 2011-07-28
Is your permissions menu different to the image attached to this post?.

---

### Post by fdrake on 2011-07-28
```
sudo chmod +x /path/of/file.exe
```
make the file executable
and then
```
wine /path/of/file.exe
```

---

### Post by ProfessorUnicorn on 2011-07-28
> **lmarmisa said:**
> Is your permissions menu different to the image attached to this post?.

When I right click on a file, and go to properties, it looks like this:

---

### Post by ProfessorUnicorn on 2011-07-28
> **fdrake said:**
> ```
sudo chmod +x /path/of/file.exe
```
make the file executable
and then
```
wine /path/of/file.exe
```

I'm so confused. I can not even find the Path of files anymore. I think when I used Ubuntu I could just right click on the file and go to properties and it would show me the path. With Xubuntu I have no idea what I'm doing. -_-

---

### Post by lmarmisa on 2011-07-28
Sorry. My last capture was wrong. I attach here the correct image.

I think your problem is related to read/write permissions. Try to copy your exe or java file to the desktop and open its properties. If you downloaded a zip file, extract the contents to physical files. Do not try to change permissions to the contents of a zip file. The system will not allow to do that.

---

### Post by ProfessorUnicorn on 2011-07-28
Haha that's alright. I extracted the folder with the file to the desktop and tried it. It's still the same.  How would I find the path of the file in XFCE so I can do the command fdrake suggested?

---

### Post by lmarmisa on 2011-07-28
> **ProfessorUnicorn said:**
> Haha that's alright. I extracted the folder with the file to the desktop and tried it. It's still the same.  How would I find the path of the file in XFCE so I can do the command fdrake suggested?

Try this command:

```

cd ~/Desktop
chmod +x yourfile.exe_or_java

```

---

### Post by NERDMAN! on 2011-07-28
unfortunately the option to mark a file as executable from the properties window is non existent in xfce4, which is the default version of xfce that comes with xubuntu as of 10.04 onwards. so commandline is really the only way to go, its a minor inconvenience considering the raw performance you get out of xfce.

the path of file is simply the directory the file is in, example /home/yourname/downloads/yourfile.exe

your in xfce4 doubtlessly so you should have an option in your context (right click menu) marked "open terminal here"
use that, then use command 
```
chmod +x file.exe
```

if you dont have said option, open terminal from your applications menu,
then use the change directory command to navigate to the file,
it usually starts you off in your home directory, and for the sake of an example your file is in the downloads folder so an example of the command would be

```
cd downloads
chmod +x filename.exe 
```

hope this helps. throw us another post if it doesnt and include screenshots of exactly what your doing, and of the terminal window output, and we will see what we can do.

---

### Post by ProfessorUnicorn on 2011-07-28
Thanks everyone for your support! I finally got it figured out with NERDMAN!'s suggestion to use the "Open terminal Here" option. :D

---

