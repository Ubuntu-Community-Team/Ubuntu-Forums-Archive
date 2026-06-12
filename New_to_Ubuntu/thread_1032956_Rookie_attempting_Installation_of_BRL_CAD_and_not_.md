---
title: "Rookie attempting Installation of BRL CAD and not successful"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Neocssck on 2009-01-06
Looked thru other similar threads and couldn't find any relevant help. I downloaded and unpacked the tar.gz for BRL CAD onto my Desktop, and that's about all I could figure out to do. Internet searches came back with nothing helpful. Help?

---

### Post by 73ckn797 on 2009-01-06
> **Neocssck said:**
> Looked thru other similar threads and couldn't find any relevant help. I downloaded and unpacked the tar.gz for BRL CAD onto my Desktop, and that's about all I could figure out to do. Internet searches came back with nothing helpful. Help?


Was the uncompressed file a "deb" extension?

---

### Post by Neocssck on 2009-01-07
Filename is brlcad_7.12.2_sgi_ia64.tar.gz, so no?

---

### Post by linux_tech on 2009-01-07
Install guide here-
[http://www.brlcad.com/downloads/documentation/BRLCAD_VolumeI.pdf](http://www.brlcad.com/downloads/documentation/BRLCAD_VolumeI.pdf)

---

### Post by Neocssck on 2009-01-07
> **linux_tech said:**
> Install guide here-
[http://www.brlcad.com/downloads/documentation/BRLCAD_VolumeI.pdf](http://www.brlcad.com/downloads/documentation/BRLCAD_VolumeI.pdf)

Yea, found that a long time ago. The FTP site referenced is no longer up. They are going thru sourceforge, if I remember right from yesterday (long day). That gives a tar file, which I can untar, but can't find any make file, installation program, or anything, which is why I'm asking the pros. Attempted to straight copy the files in the brl cad /usr/bin to the actual /usr/bin, and with all the other files. Then tried running mged, or whatever the name of the run file for the main program, and got nothing.

/Like I said before, I'm tired, so I may have dorked up some names/filepaths.

---

### Post by 73ckn797 on 2009-01-08
> **Neocssck said:**
> Filename is brlcad_7.12.2_sgi_ia64.tar.gz, so no?


tar.gz files are compressed files like PKZIP. I was asking what were the names of the files **_*in*_** the tar.gz file. Were there any ".deb" files?

---

### Post by Neocssck on 2009-01-08
> **73ckn797 said:**
> tar.gz files are compressed files like PKZIP. I was asking what were the names of the files **_*in*_** the tar.gz file. Were there any ".deb" files?

Oh, oops, I misunderstood. My apologies. No I didn't see anything. Knew enough to check for that.

---

### Post by 73ckn797 on 2009-01-08
> **Neocssck said:**
> Oh, oops, I misunderstood. My apologies. No I didn't see anything. Knew enough to check for that.


I downloaded the file you are talking about. It appears to be just straight program files in a /usr directory. I did not download other information files I saw on their site. I assume that you looked onto their other information.  The installation pdf is available. I looked at it but it is assuming the file is in a different format. I am not versed on using "rpm" files or installing those types.

---

### Post by jestal on 2009-07-01
I downloaded the same file.
./configure seems to work.
make errors with 

/usr/bin/ld: cannot find -ltk8.5
collect2: ld returned 1 exit status
make[2]: *** [libdm.la] Error 1
make[2]: Leaving directory `/brlcad-7.14.8/src/libdm'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/brlcad-7.14.8/src'
make: *** [all-recursive] Error 1

---

