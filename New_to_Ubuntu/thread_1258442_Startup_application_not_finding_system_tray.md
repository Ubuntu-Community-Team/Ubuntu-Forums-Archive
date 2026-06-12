---
title: "Startup application not finding system tray"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-09-05
I'm using Skype Call Recorder along with Skype.  Since upgrading to 9.04, I'm getting a warning at startup that this application is not finding my system tray.  Is there any way that I can delay this (or any) application from loading at startup for like 10-15 seconds? :confused: Thanks!!!

---

### Post by mac9416 on 2009-09-06
Is this program run in a startup script? If so, you can change it from something like
```
command-name
```
to
```
sleep 10 && command-name
```

That will cause the program to start after a delay of 10 seconds.

Hope that helps.
-mac

---

### Post by mac9416 on 2009-09-06
[http://ubuntuforums.org/showthread.php?t=104473](http://ubuntuforums.org/showthread.php?t=104473)
Someone there managed to do it like this:
> I managed to make it work by creating a text file with the following:
Code:

```
#/bin/bash
sleep 9 && amule
```

And pointed to that on System | Preferences | Sessions -> Startup Programs

---

