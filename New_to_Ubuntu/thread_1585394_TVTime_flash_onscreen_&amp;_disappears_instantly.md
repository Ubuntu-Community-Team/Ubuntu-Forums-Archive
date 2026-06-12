---
title: "TVTime flash onscreen &amp; disappears instantly"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-09-30
Is this fixable?

mark@Lexington-19-Karmic:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/mark/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/mark/.tvtime/tvtime.xml: Permission denied.
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument
videoinput: Can't read frame. Error was: Invalid argument (0).
videoinput: Can't read frame. Error was: Invalid argument (0).
Found "USB Device 0x46d:0x807 : USB Audio (hw:1,0)"
I/O error : Permission denied
I/O error : Permission denied
videoinput: Can't read frame. Error was: Invalid argument (0).
videoinput: Can't read frame. Error was: Invalid argument (0).
videoinput: Can't mute card.  Post a bug report with your
videoinput: driver info to [http://tvtime.net/](http://tvtime.net/)
videoinput: Include this error: 'Invalid argument'

---

### Post by Mark_in_Hollywood on 2010-10-01
I see that 40 people have looked at my problem and no one knows how to resolve it. I'm closing this post to prevent others from taking time needlessly.

Thank you, Community.

---

### Post by zoli4290 on 2010-10-15
There is a known bug in Ubuntu since Karmic which is still present in Maverick (see [https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/552060](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/552060)). It is about a PCI tv-card and a USB sound device.
You may be able to correct it with a patch from here: [https://launchpad.net/~whoopie79/+archive/testing/+packages](https://launchpad.net/~whoopie79/+archive/testing/+packages)

---

