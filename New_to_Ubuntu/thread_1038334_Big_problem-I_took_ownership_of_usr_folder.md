---
title: "Big problem-I took ownership of usr folder"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-12
I know there is a thread for this, but I can't find it. So here is my problem. I accidentally took ownership of my usr directory. One of the things that this caused, was loss of my sudo. And of course, all the fixes I could find that didn't require using the cd, did require sudo. A post said use the cd and enter the recovery mode. There isn't on on my cd. However, on my first attempt to fix this I putzed around and managed to get to a command line without actually booting the cd. I mean I got to a command line during the boot process. I don't remember how I did it though. So I typed
```
ls -l usr/bin/sudo
```
That gave me daniel daniel for ownership, so I chowned it and got root root. So I re-booted the computer. During re-boot I got messages. "users home/.dmrc is being ignored. User needs to own this dir and have 644 permisions" I open this file to see what it was, and it was empty. I also got "couldn't update ICEauthorazation file. /home/daniel/ICEauthorization" So, I need to know how to get back to that command line when starting the cd. I also need to know how to change the permission (mode?) I tried chmod when I re-booted without the cd, but I have so many issues it didn't work. Oh, it told me 644 was (not a permission mode?) Any and all help will be appreciated...and needed..lol. I am running Intrepid, by the way.
[COLOR="White"]aa
[/COLOR]

---

