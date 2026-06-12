---
title: "make command"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-02-07
Lately every time I try install a tar program I am running into trouble.  This has happened for the last three or four times and I am about to give up.

I type:

 tar -xzvf filename.tar.gz

The program will then decompress.  I then cd  to the folder that it creates and type:

./configure

The program then goes through a long list and configures.  Then the INSTALL instructions always say to type this:

make

Every time I type this command I get:

make: *** No targets specified and no makefile found.  Stop.


What am I doing wrong?

---

### Post by mushwars on 2010-02-07
can you post an ls -al of that folder?

---

### Post by Paqman on 2010-02-07
> **dondiego2 said:**
> Lately every time I try install a tar program I am running into trouble.  This has happened for the last three or four times and I am about to give up.


You should really ever need to install from a tarball, except in exceptional circumstances (or for REALLY obscure software).

Have you checked that your app isn't available from the repos, a PPA, or as a .deb?

---

### Post by dondiego2 on 2010-02-07
> **mushwars said:**
> can you post an ls -al of that folder?

carl@carl-desktop:~/Downloads/madplay-0.15.2b$ ls -al
total 2408
drwxr-xr-x 6 carl carl   4096 2010-02-07 15:09 .
drwxr-xr-x 7 carl carl   4096 2010-02-07 15:08 ..
-rw-r--r-- 1 carl carl  53838 2004-02-16 20:56 ABOUT-NLS
-rw-r--r-- 1 carl carl   4603 2004-02-23 16:34 abxtest
-rw-r--r-- 1 carl carl   3513 2004-01-23 04:41 abxtest.1
-rw-r--r-- 1 carl carl 242769 2004-02-23 16:35 aclocal.m4
-rw-r--r-- 1 carl carl   7180 2004-01-23 04:41 audio_aiff.c
-rw-r--r-- 1 carl carl   8605 2004-02-23 16:35 audio_alsa.c
-rw-r--r-- 1 carl carl  22946 2004-01-23 04:41 audio.c
-rw-r--r-- 1 carl carl   7456 2004-01-23 04:41 audio_carbon.c
-rw-r--r-- 1 carl carl   3200 2004-01-23 04:41 audio_cdda.c
-rw-r--r-- 1 carl carl   3824 2004-01-23 04:41 audio_empeg.c
-rw-r--r-- 1 carl carl   3537 2004-01-23 04:41 audio_esd.c
-rw-r--r-- 1 carl carl   3526 2004-01-23 04:41 audio.h
-rw-r--r-- 1 carl carl   3381 2004-01-23 04:41 audio_hex.c
-rw-r--r-- 1 carl carl   8432 2004-01-23 04:41 audio_jaguar.c
-rw-r--r-- 1 carl carl   6204 2004-01-23 04:41 audio_nas.c
-rw-r--r-- 1 carl carl   2468 2004-01-23 04:41 audio_null.c
-rw-r--r-- 1 carl carl   6336 2004-01-23 04:41 audio_oss.c
-rw-r--r-- 1 carl carl   5406 2004-01-23 04:41 audio_qnx.c
-rw-r--r-- 1 carl carl   3086 2004-01-23 04:41 audio_raw.c
-rw-r--r-- 1 carl carl   4762 2004-01-23 04:41 audio_snd.c
-rw-r--r-- 1 carl carl   5198 2004-01-23 04:41 audio_sun.c
-rw-r--r-- 1 carl carl   6350 2004-01-23 04:41 audio_wave.c
-rw-r--r-- 1 carl carl   8751 2004-01-23 04:41 audio_win32.c
-rw-r--r-- 1 carl carl   9850 2004-02-23 16:34 CHANGES
-rwxr-xr-x 1 carl carl  42918 2004-02-16 20:56 config.guess
-rw-r--r-- 1 carl carl   9716 2004-02-23 16:37 config.h.in
-rw-r--r-- 1 carl carl  81054 2010-02-07 15:09 config.log
-rwxr-xr-x 1 carl carl  14987 2004-02-16 20:56 config.rpath
-rwxr-xr-x 1 carl carl  30925 2004-02-16 20:56 config.sub
-rwxr-xr-x 1 carl carl 932058 2004-02-23 16:36 configure
-rw-r--r-- 1 carl carl  11567 2004-02-23 16:34 configure.ac
-rw-r--r-- 1 carl carl  17992 2000-02-27 21:31 COPYING
-rw-r--r-- 1 carl carl    900 2004-01-23 04:28 COPYRIGHT
-rw-r--r-- 1 carl carl   4600 2004-02-16 21:26 crc.c
-rw-r--r-- 1 carl carl    973 2004-02-16 21:26 crc.h
-rw-r--r-- 1 carl carl   4636 2004-02-23 16:34 CREDITS
-rwxr-xr-x 1 carl carl  13303 2003-03-28 05:44 depcomp
-rw-r--r-- 1 carl carl   7021 2004-02-16 21:26 filter.c
-rw-r--r-- 1 carl carl   1798 2004-02-16 21:26 filter.h
-rw-r--r-- 1 carl carl   4520 2002-05-05 05:41 getopt1.c
-rw-r--r-- 1 carl carl  34090 2002-05-05 05:41 getopt.c
-rw-r--r-- 1 carl carl   6458 2002-05-05 05:41 getopt.h
-rw-r--r-- 1 carl carl   3049 2003-04-18 20:32 gettext.h
-rw-r--r-- 1 carl carl   2136 2004-01-23 04:41 global.h
-rw-r--r-- 1 carl carl   7832 2000-02-28 01:21 INSTALL
-rwxr-xr-x 1 carl carl   6315 2003-03-28 05:44 install-sh
drwxr-xr-x 2 carl carl   4096 2004-02-23 17:10 intl
-rwxr-xr-x 1 carl carl 203688 2010-02-07 15:09 libtool
-rw-r--r-- 1 carl carl 182752 2004-02-16 20:56 ltmain.sh
drwxr-xr-x 2 carl carl   4096 2004-02-23 17:10 m4
-rw-r--r-- 1 carl carl   7647 2004-01-23 04:41 mad123.c
-rw-r--r-- 1 carl carl   7433 2004-01-23 04:41 madmix.c
-rw-r--r-- 1 carl carl  18454 2004-02-23 16:34 madplay.1
-rw-r--r-- 1 carl carl  19865 2004-02-23 16:34 madplay.c
-rw-r--r-- 1 carl carl    615 2003-06-04 19:39 madplay.list.in
-rw-r--r-- 1 carl carl   1433 2004-01-23 04:41 madtag.1
-rw-r--r-- 1 carl carl   3336 2004-01-23 04:41 madtag.c
-rw-r--r-- 1 carl carl   5503 2004-01-23 04:41 madtime.c
-rw-r--r-- 1 carl carl   3278 2004-02-23 16:34 Makefile.am
-rw-r--r-- 1 carl carl  34923 2004-02-23 16:36 Makefile.in
-rwxr-xr-x 1 carl carl  10270 2003-03-28 05:44 missing
-rwxr-xr-x 1 carl carl   1988 2004-02-16 20:56 mkinstalldirs
drwxr-xr-x 2 carl carl   4096 2004-02-23 17:10 msvc++
-rw-r--r-- 1 carl carl  65004 2004-02-23 16:34 player.c
-rw-r--r-- 1 carl carl   4270 2004-02-23 16:34 player.h
drwxr-xr-x 2 carl carl   4096 2004-02-23 17:10 po
-rw-r--r-- 1 carl carl   5098 2004-01-23 04:41 README
-rw-r--r-- 1 carl carl   3149 2004-01-23 04:41 resample.c
-rw-r--r-- 1 carl carl   1257 2004-01-23 04:41 resample.h
-rw-r--r-- 1 carl carl   1956 2004-02-23 16:34 rgain.c
-rw-r--r-- 1 carl carl   1876 2004-02-23 16:34 rgain.h
-rw-r--r-- 1 carl carl   1239 2004-01-23 04:41 strcasecmp.c
-rw-r--r-- 1 carl carl   1310 2004-01-23 04:41 strncasecmp.c
-rw-r--r-- 1 carl carl   7259 2004-02-23 16:34 tag.c
-rw-r--r-- 1 carl carl   1712 2004-01-23 04:41 tagger.c
-rw-r--r-- 1 carl carl   1149 2004-01-23 04:41 tagger.h
-rw-r--r-- 1 carl carl   4120 2004-02-23 16:34 tag.h
-rw-r--r-- 1 carl carl    801 2004-02-16 21:26 TODO
-rw-r--r-- 1 carl carl    101 2004-02-23 01:42 VERSION
-rw-r--r-- 1 carl carl   3598 2004-01-23 04:41 version.c
-rw-r--r-- 1 carl carl   1324 2004-02-23 16:34 version.h

---

### Post by dondiego2 on 2010-02-07
> **Paqman said:**
> You should really ever need to install from a tarball, except in exceptional circumstances (or for REALLY obscure software).

Have you checked that your app isn't available from the repos, a PPA, or as a .deb?


I checked the Ubuntu software center from the Applications menu - I don't know the other things you are talking about.  I have just been running Ubuntu for about a month.

---

### Post by oldos2er on 2010-02-07
./configure has to complete successfully before make will work. Can you post the terminal output of ./configure ?

---

### Post by semi_fiction on 2010-02-07
Do you have the build-essentials package installed?

---

### Post by dondiego2 on 2010-02-08
I appreciate all the help but I gave up.  I went back to the thread sticky posts and started reading.  I realize that I need to help myself a little bit so I went through the media set up post and fixed a lot of my problems - thanks for that!

I am now starting to read some of the 20-free books that are mentioned.  After I read a few of these maybe I'll be a little more knowledgeable and not ask the same silly questions that all us newbies ask ;)

I think I just need to spend some time learning Linux and Ubuntu.  After all, I didn't learn Windows instantly.  

Thanks for your patience.

---

### Post by oldos2er on 2010-02-08
These aren't silly questions; no one is born knowing these things.

---

