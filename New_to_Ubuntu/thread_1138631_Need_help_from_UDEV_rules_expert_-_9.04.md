---
title: "Need help from UDEV rules expert - 9.04"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by anewguy on 2009-04-26
Please see this post for the problem I have encountered.  First things changed either I think in Feisty, now they have changed again and placed the things in /lib/udev/rules.  In addition, no matter where I put my file (or it's "number" range) it doesn't seem to work now.  Did the syntax change again?

The problem - special USB devices that require special permissions file to get mounted with world permissions - they default to being owned by root which doesn't allow a normal user to access them.  They are accessed via special code using calls in the development lib for libusb.

Excuse the pointing to another open post - I don't mean to double-post, but I don't think this problem is one that a normal user would run into, and hence the existing post isn't getting attention:

[http://ubuntuforums.org/showthread.php?t=1137779]("http://ubuntuforums.org/showthread.php?t=1137779")


Please excuse this as a duplicate - if a moderator could add the existing thread to the end of this thread it would be great.

Thanks in advance

Dave :)

EDIT:  The symptoms are the same as the last time they made changes to the udev syntax - my device is not seen at all by a normal user, only by root.  Previously setting up a new rules file in udev fixed that - now it doesn't seem to anymore.  What gives????

---

