---
title: "Getting Ubuntu to decrypt dvds"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Pikzilla on 2010-01-02
Hey, I've been following this guide ([http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html](http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html)) to get my Ubuntu to be able to decrypt DVDS, but when I try to download the libdvdcss2 package with the 
sudo  /usr/share/doc/libdvdread3/examples/install-css.sh command, I end up getting  "sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found"


What's going on?

---

### Post by xtjacob on 2010-01-02
You could run this instead: ```
sudo aptitude install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh
``` I got it from [http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/](http://theindexer.wordpress.com/2009/10/25/to-do-list-after-installing-ubuntu-9-10-aka-karmic-koala/)

---

### Post by 73ckn797 on 2010-01-02
I believe that if you follow the instruction here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu), you should be able to accomplish what you desire. That is if you want to watch DVD's.

---

### Post by Dayofswords on 2010-01-02
> **73ckn797 said:**
> i believe that if you follow the instruction here: [https://help.ubuntu.com/community/medibuntu](https://help.ubuntu.com/community/medibuntu), you should be able to accomplish what you desire. That is if you want to watch dvd's.

+1

---

### Post by marshmallow1304 on 2010-01-02
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Follow "Adding the Repository" and "Playing Encrypted DVDs".



Edit: Too late; blast!

---

### Post by 73ckn797 on 2010-01-02
> **marshmallow1304 said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Follow "Adding the Repository" and "Playing Encrypted DVDs".



Edit: Too late; blast!

Hey, you did clarify the procedure.

---

### Post by slooksterpsv on 2010-01-02
You could install the Ubuntu Restricted Extras - It includes the DVD playback as well libdvdcss2

---

### Post by SPazzo on 2010-01-03
Wait!  Are you talking about playing crypted DVDs, or copying crypted DVDs?  If it's the latter I think there's a rule against answering it in this message board.  (Because of legality.)

---

### Post by Dayofswords on 2010-01-03
the guide he followed was for playing not copying, so i dont think we're breaking any rule

---

### Post by Phil Urich on 2011-01-01
> **Dayofswords said:**
> the guide he followed was for playing not copying, so i dont think we're breaking any rule

It could be quite legal to copy the DVDs too, no? I know personally my country has no laws against making one's own backups (which I am doing now, for instance; the Yann Tiersen tour DVD I have is starting to look like it's separating, so I'm making a backup .iso and video files to boot so that I can play back the video without fear of the disc dying).

---

### Post by mikewhatever on 2011-01-02
> **slooksterpsv said:**
> You could install the Ubuntu Restricted Extras - It includes the DVD playback as well libdvdcss2

You mean the libdvdnav4 and libdvdread4 packages? Don't think they are enough though.
From libvdvdread4 description:
> libdvdread probes for libdvdcss at runtime and if found, will use it to decrypt sections of the DVD as necessary. libdvdcss needs to be installed from third-party repositories (see README.Debian), it's not included in Debian.


---

### Post by slooksterpsv on 2011-01-04
> **mikewhatever said:**
> You mean the libdvdnav4 and libdvdread4 packages? Don't think they are enough though.
From libvdvdread4 description:

I mis-typed it. I meant to say you could install the restricted extras and it will install libdvdread4, which you can use to install libdvdcss2. But that's all in that article.

I know some DVDs won't play on my machine (Toy Story 3) cause of a different kind of encryption or something. Other DVDs work just fine. So I dunno on this one

---

