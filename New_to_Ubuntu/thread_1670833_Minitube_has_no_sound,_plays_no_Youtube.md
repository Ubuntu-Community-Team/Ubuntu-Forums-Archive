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

### Post by JohnHeikkila on 2011-01-19
Hey,
You could try opening your package manager (e.g. Synaptic), then finding and installing the packages "phonon-backend-gstreamer", "gstreamer-ffmpeg" and "gstreamer-plugins-bad".

By the way, are you using an 64-bit or 32-bit version of Ubuntu (or don't know)?

---

### Post by JohnHeikkila on 2011-01-19
Hey,
You could try opening your package manager (e.g. Synaptic), then finding and installing the packages "phonon-backend-gstreamer", "gstreamer-ffmpeg" and "gstreamer-plugins-bad".

By the way, are you using an 64-bit or 32-bit version of Ubuntu (or don't know)?

---

### Post by JohnHeikkila on 2011-01-19
Hey,
You could try opening your package manager (e.g. Synaptic), then finding and installing the packages "phonon-backend-gstreamer", "gstreamer-ffmpeg" and "gstreamer-plugins-bad".

By the way, are you using an 64-bit or 32-bit version of Ubuntu (or don't know)?

---

### Post by JohnHeikkila on 2011-01-19
Hey,
You could try opening your package manager (e.g. Synaptic), then finding and installing the packages "phonon-backend-gstreamer", "gstreamer-ffmpeg" and "gstreamer-plugins-bad".

By the way, are you using an 64-bit or 32-bit version of Ubuntu (or don't know)?

EDIT: Oh dear, didn't mean to make that many replies. Something happened to my internet and I wasn't aware that I had sent the reply :/

---

### Post by eckko on 2011-01-19
> **romy.mathew said:**
> 
 phonon-backend-gstreamer depends on libphonon4 (= 4:4.2.0-2); however:
  Version of libphonon4 on system is 4:4.6.2-0ubuntu5.1.
 phonon-backend-gstreamer depends on libqt4-opengl (>= 4.4.3); however:
  Package libqt4-opengl is not installed.

Can anyone suggest a more easy method to solve this issue.


Thanks

sudo apt-get install libqt4-openql | sudo dpkg --install phonon-backend-gstreamer_4.2.0-2_amd64.deb 

or

sudo apt-get install libqt4-openql phonon-backend-gstreamer

maybe?

---

