---
title: "Problem with DVD playback"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Bigmon on 2009-01-04
Spent days trying to play a dvd in ubuntu. Used every method and every media player. Then I stumbled on this:


For those of you who previously played DVDs in GNU/Linux or Windows, but for some reason are unable to now, it could be related to faulty leads/connectors, but give this one last software-related method a try:

sudo apt-get install build-essential debhelper fakeroot

then:

sudo /usr/share/doc/libdvdread3/install-css.sh

or if you get an error with that command:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

CAN ANYONE TELL ME WHAT THIS DID ? I AM POSTING THIS MESSAGE SO AS TO MAYBE HELP OTHERS WITH SIMILAR PROBLEMS !!!!
CHEERS.

---

### Post by jken146 on 2009-01-04
Go to [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories) and follow the instructions there.  Then install the package *libdvdcss2* and that should do it!

---

### Post by HotShotDJ on 2009-01-04
> **Bigmon said:**
> sudo /usr/share/doc/libdvdread3/examples/install-css.sh

CAN ANYONE TELL ME WHAT THIS DID ? I AM POSTING THIS MESSAGE SO AS TO MAYBE HELP OTHERS WITH SIMILAR PROBLEMS !!!!
CHEERS.It installed libdvdcss2.  There is a much easier way to do that -- follow the link given by jken146.

---

