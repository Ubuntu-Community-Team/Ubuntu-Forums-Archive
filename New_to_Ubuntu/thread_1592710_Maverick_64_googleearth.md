---
title: "Maverick 64 googleearth"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by alphacrucis2 on 2010-10-10
I had been have trouble getting googleearth 5.2 to work on Lucid 64 bit so I have upgraded to MM. Installed googleearth via the googleearth-package method. No joy after installing the resulting deb. I guess I will have to wait until medibuntu put up a MM package for ge 5.2.

Here's the result for the googleearth-package method

```
laptop:~$ googleearth

(<unknown>:6423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6423): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6423): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6423): Gtk-WARNING **: Loading IM context type 'ibus' failed
googleearth-bin: ../../src/xcb_io.c:452: _XReply: Assertion `!dpy->xcb->reply_data' failed.
Google Earth has caught signal 6.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/blah/.googleearth/crashlogs/crashlog-4cb26e08.txt

Please include this file if you submit a bug report to Google.
```

Nice that google are apologetic :lolflag:.

Crashlog

```
Major Version 5
Minor Version 2
Build Number 0001
Build Date Sep  1 2010
Build Time 11:25:42
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 35
OS Patch Version 0
Crash Signal 6
Crash Time 1286761992
Up Time 6.89565

Stacktrace from glibc:
/usr/lib/googleearth/libgoogleearth_free.so(+0xd090b)[0xf772490b]
[0xf777d400]
/lib32/libc.so.6(abort+0x182)[0xf5790e42]
/lib32/libc.so.6(__assert_fail+0xf8)[0xf5786878]
/usr/lib32/libX11.so.6(_XReply+0x352)[0xf4bbe282]
/usr/lib32/libGL.so.1(AtiCallFGLComposite+0xf5)[0xf483688b]
```

Don't know if this is google's fault or AMD/ATI. I am running the Ubuntu prerelease version of Catalyst 10.10.

---

### Post by oldos2er on 2010-10-10
Have you tried installing GoogleEarthLinux.bin, downloaded from google? It's worked for me.

---

### Post by alphacrucis2 on 2010-10-10
> **oldos2er said:**
> Have you tried installing GoogleEarthLinux.bin, downloaded from google? It's worked for me.

Will give that a go.

---

### Post by schworak on 2010-11-14
I tried downloading right from Google and still get the same error

**/usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64**

Did it fix the problem for you? If so, how? Did you have to do something special to remove all previous references to Google Earth?

---

### Post by faisalsadaf on 2010-11-24
This issue (according to my research) is related to either the ia32-libs libraries, or your video card).

I have a similar issue, trying to install a 32 bit application (Alfresco Bitnami native installer) on a Ubuntu 10.10 amd64 VM, running on VMWare.

If anyone has any ideas on how to fix this, besides changing file permissions, or using an older version of ia32-libs (20090808ubuntu4), please do enlighten me. I have spent the last few hours trying to get this to work, and have almost given up on this option.

Thanks!

---

### Post by schworak on 2010-11-26
> **faisalsadaf said:**
> This issue (according to my research) is  related to either the ia32-libs libraries, or your video card).

I have a similar issue, trying to install a 32 bit application (Alfresco  Bitnami native installer) on a Ubuntu 10.10 amd64 VM, running on  VMWare.

If anyone has any ideas on how to fix this, besides changing file  permissions, or using an older version of ia32-libs (20090808ubuntu4),  please do enlighten me. I have spent the last few hours trying to get  this to work, and have almost given up on this option.

Thanks!


YOU ROCK!

It looks like there was a video driver update and I simply didn't think  to go look for it. I only installed Ubuntu a few months ago and got a  new driver at that point. So for me, the problem is solved with the new  driver!

---

### Post by chris.olive on 2010-11-27
I have driven myself to the edge of madness trying to get this to work on a desktop, worked fine until a few days ago, works on a laptop no problems, but no matter what I try I get this 
> Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
My Places Path: "/home/user/.googleearth"
Cache Path: "/home/user/.googleearth/Cache"
click O.K. and the googleearth window opens but no "earth" and no search faculty, I have tried adding the files to home/user/ but no joy.
Any ideas?

---

### Post by schworak on 2010-11-27
> **chris.olive said:**
> I have driven myself to the edge of madness trying to get this to work on a desktop, worked fine until a few days ago, works on a laptop no problems, but no matter what I try I get this 

click O.K. and the googleearth window opens but no "earth" and no search faculty, I have tried adding the files to home/user/ but no joy.
Any ideas?


I'm no expert, but it sounds like the app doesn't have proper access rights to the folder. So it tries to create it and fails.

Check the rights on your home folder. View all hidden files and see if there is a .googleearth path in you home folder. If so, check the protection properties. On my system, I have read/write access but the group and everyone else has no access. If you can't get the properties right you can always delete the folder. If it isn't there at all, check the rights to your home folder. Just wondering if they got messed up some how.

---

