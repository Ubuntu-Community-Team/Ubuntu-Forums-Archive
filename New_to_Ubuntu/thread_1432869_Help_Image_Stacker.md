---
title: "Help: Image Stacker"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by arma0012 on 2010-03-18
I'm trying to find a decent package to automatically merge a stack of images on a single subject with varying focus, to make a composite image entirely in focus. All I could find is the 'Stack focuser' plugin for ImageJ. While ImageJ installed fine, when I downloaded the plugin, and tried to copy it to the plugins folder as the [website]("http://rsb.info.nih.gov/ij/plugins/stack-focuser.html") described, I received this error:
[HTML]sam@angus:~$ cp -v /home/sam/Downloads/Stack_Focuser_.class /usr/share/imagej/plugins/
`/home/sam/Downloads/Stack_Focuser_.class' -> `/usr/share/imagej/plugins/Stack_Focuser_.class'
cp: cannot create regular file `/usr/share/imagej/plugins/Stack_Focuser_.class': Permission denied
[/HTML]Does anyone have any idea as to how to remedy this?

Alternatively, is there any other decent image stacking programs available?

Cheers,
Sam

---

### Post by wjm on 2010-03-18
double post

---

### Post by wjm on 2010-03-18
need to use sudo to copy files to /usr/share - it can't be done by normal users.

---

### Post by arma0012 on 2010-04-05
Thanks for your help, stacker works great.

Sorry for late reply.

Cheers,
Sam

---

