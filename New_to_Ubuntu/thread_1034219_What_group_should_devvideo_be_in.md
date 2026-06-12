---
title: "What group should /dev/video* be in?"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by Nerdriot on 2009-01-08
Sort of random question, but I can't find the answer anywhere.

I have a webcam that works using luvcview, and in aMSN, but when I test it with Camorama, it says it couldn't connect to /dev/video0. I read in another post somewhere to add your user to the group /dev/video* is a part of, but when I run ls -la on /dev/video*, I get this:

```
crw-rw----+ 1 root 44 81, 0 2009-01-08 02:28 /dev/video0

```

It doesn't seem like I don't have *permission* to access it, just that it won't for some reason.

Regardless, I noticed that there was no group for /dev/video*, and it confused me.

Anyone know what group it SHOULD be in? Or should I make one for it?

---

### Post by sdennie on 2009-01-08
1) It's in group 44.  On Ubuntu, that group is also known as "video" unless you have significantly changed /etc/group.

2) If you are using uvcvideo, your problem with camorama is probably that camorama expects v4l whereas the uvcvideo driver is probably only supporting v4l2.  This happens to me as well.  The solution is to use cheese instead of camorama:

```

sudo apt-get install cheese

```

---

### Post by Nerdriot on 2009-01-08
Well, that was my first app I tried with (the one I was most familiar with). And you're right; it is v4l2. It's a Logitech Quickcam. I'm pretty shocked even luvcview picks it up, as I've read a lot of complaints about compatibility.

Anyway, cheese gives me the "test" screen mostly, unless I go to ""Recording", where it goes to just a black screen.

I've checked gstreamer-properties, and set up the video portion correctly based on lsusb's output of where the camera is, but I get this:

```
Failed to construct test pipeline for 'Video for Linux 2 (v4l2)'
```

Any idea what might be causing that?

---

### Post by sdennie on 2009-01-08
Actually, I'm not sure.  What is the output of:

```

grep video /etc/group

```

Is your user name there?  Is there any output at all?

---

### Post by Nerdriot on 2009-01-08
Yeah, root is there, and my user is. I added it when I thought it might be due to me not having access to /dev/video0, but it didn't help. I also ran cheese and camorama as root, and that didn't help, either.

I can't quite figure out the error that gstreamer-properties is giving me. I've googled it for hours..

Oh yeah, here's the output:

```
$ grep video /etc/group
video:x:1003:MyUser,root
```

---

