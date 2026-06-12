---
title: "why won't some icons work in youtube vol, full screen etc"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-07-02
hey what's up?  quick question as i have finally been able to use my 9.10 karmic to do pretty much everything i want.  i can happily say that i am only using win 7 for my itunes cuz i have a 5th gen nano. (another story for another time)  i am having difficulties on certain web pages.  youtube is one but the problem is erratic.  the problem is that i can't click the volume, pause, etc, on certain youtube video's.  it's not on every video though.  just certain one's this also happens on certain web pages such as this page:

[http://carlosmiller.com/2010/06/17/11128/#comment-30652](http://carlosmiller.com/2010/06/17/11128/#comment-30652) 

on the page listed above i can't even play the video.  notice that it's a youtube video and i can't even play it on that page.  however if i go to that video on youtube it plays and i can go full screen and everything.  could someone tell me what i need to do in order to remedy this?

---

### Post by kimikrishna on 2010-07-02
> **bradmayne04 said:**
>  i can happily say that i am only using win 7 for my itunes

Not a solution to your problem. 
You can use banshee instead of i tunes ..

---

### Post by marshmallow1304 on 2010-07-02
See the workarounds on the [bug report]("https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407?comments=all").

---

### Post by lovinglinux on 2010-07-02
This usually happens when you are using the 32bit plugin on a 64bit system.

To fix that you need to edit the npviewer file. Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by bradmayne04 on 2010-07-02
> **kimikrishna said:**
> Not a solution to your problem. 
You can use banshee instead of i tunes ..


i don't think banshee supports Ipod Nano 5th generation.  Maybe I'm wrong though?  Please let me know your specific experiences.  I've tried gtkpod and some others but like I said the 5th gen Ipod Nano is too new and their is no software for it yet.  (that I know of)  if you personally used software that supports this let me know ASAP!

---

### Post by bradmayne04 on 2010-07-02
> **lovinglinux said:**
> This usually happens when you are using the 32bit plugin on a 64bit system.

To fix that you need to edit the npviewer file. Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```Save the file and restart the browser.

I just did exactly as you said and it worked!  Thanks dude!! I only tried the site i posted the url for so far though but it worked no problem!!

---

### Post by lovinglinux on 2010-07-02
> **bradmayne04 said:**
> I just did exactly as you said and it worked!  Thanks dude!! I only tried the site i posted the url for so far though but it worked no problem!!

You are welcome. :)

---

