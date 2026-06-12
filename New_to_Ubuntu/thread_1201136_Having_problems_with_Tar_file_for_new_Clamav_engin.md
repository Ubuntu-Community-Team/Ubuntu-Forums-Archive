---
title: "Having problems with Tar file for new Clamav engine."
date: 2009-06-30
forum: New to Ubuntu
---

### Post by songl100 on 2009-06-30
I have 9.04 jaunty jackalope running on my laptop. I downloaded the tar file for clamav's new engine: clamav-0.95.2.tar.gz. I already installed clamav and clamtk the GUI for clamav when I had 7.10. I know how to extract the file with tar and did a mistake I think by extracting this tar file on my Desktop directory. When I open clamtk, it still shows the old clamav engine 0.95.1. Wondering on where to direct the extracted files for this tar file. Also, when I run sudo freshclam I get:

song@dell-desktop:~$ sudo freshclam
ClamAV update process started at Tue Jun 30 16:58:32 2009
main.cvd is up to date (version: 51, sigs: 545035, f-level: 42, builder: sven)
Downloading daily-9521.cdiff [100%]
freshclam: relocation error: freshclam: symbol mp_init, version CLAMAV_PRIVATE not defined in file libclamav.so.6 with link time reference

First wondering where I extract the tar file so clamtk uses it. Second wondering on how to get freshclam to work. I got main.cvd updated but I get this relocation error. Any help is appreciated. Also I did use ./configure, make, and make install with sudo in front after I got errors just running the commands without sudo. - Song

---

