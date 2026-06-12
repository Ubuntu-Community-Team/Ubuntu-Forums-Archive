---
title: "Choosing &quot;open with&quot; executible file"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by Ninlama on 2010-07-20
Hi All,

I'm learning a day at a time. I like to listen to streaming classical music from FM websites. When trying to listen to the mp3 version, Firefox asks which program I want to open the file with. I want to listen using VLC. Is there an easy way to choose the program I want to use to listen to a music stream?

In Windows I would have navigated to vlc.exe in the Programs folder under Windows.

Thanks!

Ninlama

---

### Post by nmaster on 2010-07-20
you do basically the same thing in ubuntu.  just find where the vlc executable is.  if you're not sure, go to a terminal issue this command
```
 which vlc
```

---

### Post by Ninlama on 2010-07-20
That works great. Thanks for your help!!!!!

---

### Post by nmaster on 2010-07-20
another lesson (lol): be sure to tag the thread as SOLVED!

---

### Post by mcduck on 2010-07-20
> **Ninlama said:**
> 
In Windows I would have navigated to vlc.exe in the Programs folder under Windows.
While the "which" command suggested above works really  nice, you'll quickly find that pretty much for every program the executable file will be in /usr/bin. Makes sense, since that's the standard location for all executables other than system- and admin-related stuff.

So instead of running "which" you might want to first take a quick look if you can find the executable in /usr/bin/. :)

---

### Post by lkjoel on 2010-07-20
To find a file (in your case vlc), you simply type:
```
ls *folder* | grep "*file*"
```
And for your case, it would be:
```
ls /usr/bin | grep "vlc"
```

---

### Post by ajgreeny on 2010-07-20
If you installed the **mozilla-plugin-vlc** it would do that within firefox and not need to start vlc as a separate application.  Perhaps you prefer to have the extra control over which app is used each time.

---

### Post by nmaster on 2010-07-21
> **lkjoel said:**
> To find a file (in your case vlc), you simply type:
```
ls *folder* | grep "*file*"
```And for your case, it would be:
```
ls /usr/bin | grep "vlc"
```

keep in mind that this requires knowing the directory where the file might be. ls is not recursive

 if you don't know where the file is, try "locate FILE" .  this will search all files currently in the locate database.  this database is updated automatically from time to time, but you can manually do it with "sudo updatedb"

the best way to find an executable at the command line, however is by using which. for more information, check out the man page with "man which"

---

