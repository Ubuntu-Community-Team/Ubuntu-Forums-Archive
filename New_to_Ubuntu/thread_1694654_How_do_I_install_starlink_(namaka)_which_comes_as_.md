---
title: "How do I install starlink (namaka) which comes as a rpm file?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by bwallum on 2011-02-24
Hi

I'm trying to install Starlink - Namaka and have downloaded the source files from  [http://starlink.jach.hawaii.edu/starlink/NamakaDownload](http://starlink.jach.hawaii.edu/starlink/NamakaDownload)

The community help file on the subject  [https://help.ubuntu.com/community/Starlink](https://help.ubuntu.com/community/Starlink) does not work.

Can anybody help me install this package please?

---

### Post by Foxheadz on 2011-02-24
I know theres a command line application called alien that will change an rpm file into a deb file, not entirely sure on the command but im sure theres a man page.

---

### Post by uRock on 2011-02-24
What error(s) are you getting?

---

### Post by rosencrantz on 2011-02-24
Is it really an rpm install? From the instructions on the page you [linked to]("http://starlink.jach.hawaii.edu/starlink/NamakaDownload") it looks like it's precompiled and stand-alone with some workarounds for older dependencies. I can't check it right now because of the impressive download size ;-)
So, to install, you'd have to untar to some directory, do 
export STARLINK_DIR=<the same directory>, optionally install libg2c0 with apt-get, download their [libexpat-64.so.0]("http://starlink.jach.hawaii.edu/extras/libexpat-64.so.0") and put it into the lib subfolder.
No need for alien or lengthy compiling.

Good luck

rosencrantz

---

### Post by bwallum on 2011-02-25
> **rosencrantz said:**
> Is it really an rpm install? From the instructions on the page you [linked to]("http://starlink.jach.hawaii.edu/starlink/NamakaDownload") it looks like it's precompiled and stand-alone with some workarounds for older dependencies. I can't check it right now because of the impressive download size ;-)
So, to install, you'd have to untar to some directory, do 
export STARLINK_DIR=<the same directory>, optionally install libg2c0 with apt-get, download their [libexpat-64.so.0]("http://starlink.jach.hawaii.edu/extras/libexpat-64.so.0") and put it into the lib subfolder.
No need for alien or lengthy compiling.

Good luck

rosencrantz
There it was, right before my nose and I couldn't see it looking for the complexity. Thank you rosencrantz for the steer and thanks to everybody for all the contributions. Now up and running! Just a small point the libexpat-64.so.0 needs to be renamed to libexpat.so.9

---

