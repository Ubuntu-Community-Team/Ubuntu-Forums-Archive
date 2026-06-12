---
title: "prboom freedoom ?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by stevek123 on 2010-04-11
I installed Freedoom from Karmic (new fresh install) and went to id website and downloaded prboom tarball. I configured and made & installed it. It opens and instantly crashes when I try to play. I think I found a fix in this thread.
[http://ubuntuforums.org/showthread.php?t=1304237&highlight=freedoom](http://ubuntuforums.org/showthread.php?t=1304237&highlight=freedoom)

id website also mentions a sound issue with my architecture and offers a patch...but the debian link looks like the easier option.

My ?s
1) I suspect I should un-install my existing prboom before I download and employ the patched program. Since I did this thru basic instruction in the id software I am not sure how to do this. unmake/uninstall or something???
2) My comp arch is an AMD64 - but I installed the 32bit OS. When I download the deb patched file, which one do I download??? link is here.
[http://packages.debian.org/sid/prboom](http://packages.debian.org/sid/prboom)

---

### Post by Chronon on 2010-04-11
> **stevek123 said:**
> I installed Freedoom from Karmic (new fresh install) and went to id website and downloaded prboom tarball. I configured and made & installed it. It opens and instantly crashes when I try to play. I think I found a fix in this thread.
[http://ubuntuforums.org/showthread.php?t=1304237&highlight=freedoom](http://ubuntuforums.org/showthread.php?t=1304237&highlight=freedoom)

id website also mentions a sound issue with my architecture and offers a patch...but the debian link looks like the easier option.

My ?s
1) I suspect I should un-install my existing prboom before I download and employ the patched program. Since I did this thru basic instruction in the id software I am not sure how to do this. unmake/uninstall or something???
2) My comp arch is an AMD64 - but I installed the 32bit OS. When I download the deb patched file, which one do I download??? link is here.
[http://packages.debian.org/sid/prboom](http://packages.debian.org/sid/prboom)

1) If you installed using "sudo make install" then it's likely that the Makefile also contains a routine for uninstalling (usually "sudo make uninstall").  You can open the Makefile in a text editor to see if this is present.

2) If your OS is 32-bit then you need to install 32-bit applications.

---

### Post by stevek123 on 2010-04-12
wow - thanks
I found the make file in my home folder and looked thru it and to be honest I dont know what I was looking for. It looked to me like the prog uninstalled a bunch of stuff on its own at the end of the make, but I didnt see a build for 'uninstall' that I recognized. I'm pretty sure I ran it using 'sudo make install-strip' so if I run the sudo make uninstall and it works great - if that command is not recog it'll tell me - right?

as for the architecture type - just wanted to confirm to skip the amd64 file and use the file for i386.

---

### Post by Chronon on 2010-04-12
Yeah, make should complain if it doesn't recognize a "build option".  If it accepted it then I presume that it worked.

Correct.  You have a 32-bit OS, so you should install the i386 version.

---

### Post by stevek123 on 2010-04-12
Thanks again!

---

