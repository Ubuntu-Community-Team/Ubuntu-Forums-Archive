---
title: "Minitube has no sound, plays no Youtube"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by romy.mathew on 2011-01-19
Hi there was a earlier post by someone on the same issue 
h**p://ubuntuforums.org/showthread.php?t=1361315

but when i tried to install the .deb file it showed some dependency problem 

"
romy@romy-laptop:~/Downloads$ sudo dpkg --install phonon-backend-gstreamer_4.2.0-2_amd64.deb 
Selecting previously deselected package phonon-backend-gstreamer.
(Reading database ... 128229 files and directories currently installed.)
Unpacking phonon-backend-gstreamer (from phonon-backend-gstreamer_4.2.0-2_amd64.deb) ...
dpkg: dependency problems prevent configuration of phonon-backend-gstreamer:
 phonon-backend-gstreamer depends on libphonon4 (= 4:4.2.0-2); however:
  Version of libphonon4 on system is 4:4.6.2-0ubuntu5.1.
 phonon-backend-gstreamer depends on libqt4-opengl (>= 4.4.3); however:
  Package libqt4-opengl is not installed.
dpkg: error processing phonon-backend-gstreamer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phonon-backend-gstreamer

"

Can anyone suggest a more easy method to solve this issue.


Thanks

---

