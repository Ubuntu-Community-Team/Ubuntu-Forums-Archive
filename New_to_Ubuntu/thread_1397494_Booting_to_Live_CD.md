---
title: "Booting to Live CD"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by mistypotato on 2010-02-03
Hello,

I'm trying to modify my network configuration files on my Ubuntu Server by booting in with the Live CD.  My server is hanging on "Configuring Network Settings"

Problem is there seems to be only two options....

1). Rescue Mode where it appears to want to re-install the system (I do not want that yet)

2). Boot to the first Hard Drive....(not working)

How do I boot from the Live CD so that I can see the files on the Server hard drive?


Thx

---

### Post by mistypotato on 2010-02-03
ok, I finally figured it out...accidentally and with some fear of destroying the file system that was already there.

For the benefit of anyone finding this later....

Go ahead and boot the Live CD and choose the option to **Rescue a Broken System**.

You'll have to answer quite a few questions which to me appeared to be leading to a re-install, but eventually it will ask you which location you want to "Shell" into....if you're not a Linux geek, that may be confusing...just replace the word "Shell" with "Access".

If you don't already have Linux installed. choose the CD as the Shell.  Otherwise, it will show you the partitions and you can choose the one you want to access....(or shell) into.

Hope this helps

---

