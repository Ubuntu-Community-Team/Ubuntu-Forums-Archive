---
title: "Can't download updates...Help..."
date: 2009-06-17
forum: New to Ubuntu
---

### Post by sillyboy on 2009-06-17
Using 8.04.  Little orange star says "3 updates available".  When I try to install updates, I am informed: Warning  You are about to install updates that can not be authenicated.  Then , after I click install I get the message: "Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages? Y or N"

The little orange star never goes away, and I can never get the updates!  What's up with this??  Please help.  I would like very much to get away from Windows, but things like this (no explanation, and I don't have a clue), make things extremely hard for one not to want to go back to Billy's world.

Can someone simplify this for me??  I'm stupid, and not online 24/7.

Thanks

Ralph

---

### Post by LewRockwell on 2009-06-17
could you check your notes and let us know which updates you're having difficulties with?

also what repository are you updating from?

and...if everything is currently working for you then I wouldn't get too upset if it takes a little time to figure out the difficulties in your specific situation.

---

### Post by sillyboy on 2009-06-17
Please tell me want you want to know and how I can get the info you need to help me.  Ubuntu seemed so easy for awhile, then it seems I'm back in a Billy nightmare (except no BSOD's).

Thanks

---

### Post by treesurf on 2009-06-17
Open up the update manager again (the little orange star) and take note of which updates are not being installed and then let us know.

---

### Post by wpshooter on 2009-06-17
Have you tried changing to a different Ubuntu server ?

---

### Post by Therion on 2009-06-17
Try a different server or just chill out and wait a bit.  Those errors always resolve themselves after a day or two.

---

### Post by sillyboy on 2009-06-17
Distribution of updates...

libmp4v2-0

Other Updates:

------------------------------------------------------

Amorak
Bla Bla etc

Amorak-xine
bla bla ect





Description of update:

Version 1:1.6dfsg-0.2ubuntu1: 

  [ Mario Limonciello ]
  * debian/control:
    - Don't build depend on libfaac-dev or libfaad-dev.
      Readme indicates that both can cause troubles with the build.
    - Build depend on non cvs variants of libavcodec-dev and libavutil-dev
    - Update maintainer field.
    - Drop bugs field.
  * Add 04_bashishms.dpatch for a few dash/bash related problems during build.
  * Repack .orig.tar.gz to remove doc/{*.pdf,*.jpg} and 
    lib/rtp/test-libcommon for DFSG.

  [ John Dong ]
  * debian/copyright:
    - Include licenses for all included source packages.


Version 1:1.6-0.2: 

  * rebuild against the latest libx264-57


Version 1:1.6-0.1: 

  * New patch 03_typo.dpatch to fix a typo.
  * Add support for ccache.


Version 1:1.6-0.0: 

  * New upstream release.


Version 1:1.5.0.1-0.4: 

  * Change libfaad2-dev by libfaad-dev in Build-depens.


Version 1:1.5.0.1-0.3: 

  * Add aac support.


Version 1:1.5.0.1-0.2: 

  * Need to build-depends on libavutilcvs49-dev and libmp4v2-dev.


Version 1:1.5.0.1-0.1: 

  * Build only the server package.


Version 1:1.5.0.1-0.0: 

  * New upstream release.
  * Remove --disable-server from configure options and add a new
    mpeg4ip-server package.


Version 1:1.4.1-0.2: 

  * Make libesd0-dev the first package in Buil-Depends (libesd0-dev |
    libesd-dev), otherwise builder don't llike that.


Version 1:1.4.1-0.1: 

  * Move all mp4 libraries in the libmp4v2-0 package.


Version 1:1.4.1-0.0: 

  * New upstream release.
  * rename the libmp4 package to libmp4v2-0.


Version 1:1.2-0.0: 

  * This package is the real version. The previous was 0.9.8.6 from the faad
    tarball.


libmp4 (2.0.0-0.0) unstable; urgency=low

  * Initial release.

Description: (tab)

FAAD2 is the fastest ISO AAC audio decoder available. FAAD2 correctly decodes all MPEG-4 and MPEG-2 MAIN, LOW, LTP, LD and ER object type AAC files.
This package contains the MP4 (aka AAC) library.

---

### Post by treesurf on 2009-06-17
Go to System>Administration>Software Sources.  Next to the drop down menu it will say "Download from...".  Where are your updates downloading from?

---

### Post by sillyboy on 2009-06-17
[http://mirrors.acm.jhu.edu/ubuntu](http://mirrors.acm.jhu.edu/ubuntu)

treesurf: I have to turn in.  How do i keep this forum going with you so that I get results?  I will be back Friday afternoon. Sorry...

---

### Post by treesurf on 2009-06-17
Change that drop down menu to the Main Server and see if that solves your problem.  Sometimes the mirrors will be a few days behind the main server and this sort of problem arises. 

I will try to remember to check back in on this in a couple days.  Or you can just click on my username and send me a private message.  Good luck!

---

