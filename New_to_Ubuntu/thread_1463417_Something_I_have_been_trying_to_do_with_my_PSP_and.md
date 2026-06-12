---
title: "Something I have been trying to do with my PSP and PC"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by RandomP on 2010-04-26
I have custom firmware on one of my PSP's and thought it would be neat to make it so the PSP streams video to the PC. There is a program for windows called remotejoy which does that. I do not have or want windows though so I searched a bit on the net. 

I came across this video:
[http://www.youtube.com/watch?v=wbDDie7Yv58](http://www.youtube.com/watch?v=wbDDie7Yv58)

And this tutorial which goes along with that video:
[http://lgallardo.com/en/2010/02/15/remotejoy-para-linux-usando-irshell-5/](http://lgallardo.com/en/2010/02/15/remotejoy-para-linux-usando-irshell-5/)

My problem is that I cannot get the commands to work. When I try to access the directory the usbhostfs18 file is in, terminal tells me the obvious, "...is a directory"

Anyone know how I can get usbhotfs18 and the other file/folder to run properly? I already have iR shell on my PSP.

---

### Post by RandomP on 2010-04-27
No one?

---

### Post by mechro on 2010-04-27
If your downloaded files are, for example, on your Desktop then try...

```
sudo ~/Desktop/usbhostfs18
```

and...

```
~/Desktop/rj_resize_mod -c -d
```

---

