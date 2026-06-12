---
title: "Cannot Remove Software with Ubuntu Software Center in 9.10"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by IndigoMoonMan on 2009-11-02
I upgraded from 9.04 to 9.10 a few days ago.  In 9.04 I could add/remove software with no problems.  However, I just now discovered that I can no longer remove programs from the Ubuntu Software Center. It says, "Package operation failed".  In the 'details' section I got the following...

Removing aisleriot ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Setting up libboost1.38-dbg (1.38.0-6ubuntu6) ... 
/var/lib/dpkg/info/libboost1.38-dbg.postinst: 9: /usr/share/python/runtime.d/libboost1.38-dbg.rtupdate: not found 
dpkg: error processing libboost1.38-dbg (--configure): 
 subprocess installed post-installation script returned error exit status 127 
Errors were encountered while processing: 
 libboost1.38-dbg 

So I figured that libboost1.38-dbg was the problem so I went to the Synaptic Package Manager to remove it and selected 'Mark for complete removal'.  I got the following error... 

E: libboost1.38-dbg: subprocess installed pre-removal script returned error exit status 127

Any help in resolving this will be greatly appreciated

James

---

### Post by SteveDee on 2009-11-02
Yeah, there must be bugs in Ubuntu Software Centre ([http://ubuntuforums.org/showthread.php?t=1305854](http://ubuntuforums.org/showthread.php?t=1305854)) which is not what you need as a new user.

I suggest you just remove aisleriot using Synaptic for the time being (i.e. type "aisleriot" in the Synaptic Quick Search box, then mark for removal).

---

