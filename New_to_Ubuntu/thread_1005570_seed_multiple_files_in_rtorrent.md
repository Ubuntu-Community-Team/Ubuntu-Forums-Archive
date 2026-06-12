---
title: "seed multiple files in rtorrent?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by uarale on 2008-12-08
Hi,

I've changed bittorrent client from the build-in Transmission to rtorrent, the speed and lightweight are impressive.

but i noticed that only the first torrent file is in the seeding status, while the other finished ones had the zero speed of seeding. how can i do to seed more than one file at a time?

one more question: rtorrent check hash of every files after restarting, this check takes about 15 minutes for me (downloading and seeding very large files). while other clients do not perform this check, is it possible rtorrent skip that too?

---

### Post by ABCC on 2008-12-08
> **uarale said:**
> Hi,

i've changed bittorrent client from the build-in Transmission to rtorrent, the speed and lightweight are impressive.

but i noticed that only the first torrent file is in the seeding status, while the other finished ones had the zero speed of seeding. how can i do to seed more than one file at a time?

one more question: rtorrent check hash of every files after restarting, this check takes about 15 minutes for me (downloading and seeding very large files). while other clients do not perform this check, is it possible rtorrent skip that too?

You can solve those problems with a configured ~/.rtorrent.rc file. An example is located in the file /usr/share/doc/rtorrent/examples/rtorrent.rc.

The example is well documented and should help you get started. Make sure to setup a session directory aswell as this is where the torrents' d/l state is saved in. For more info see the [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/), [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/) and [http://www.wtorrent-project.org/trac/](http://www.wtorrent-project.org/trac/)

---

### Post by weezerisrock on 2008-12-08
I don't use rtorrent, (ktorrent here) but the problem sounds like rtorrent doesn't know your bandwidth so its keeping it minimal.  There should be a configuration setting page somewhere in the program (unless you have to edit the file as mentioned above), and you would have to tell it what your bandwidth is.

Hope this helps!

---

