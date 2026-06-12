---
title: "Run BitTorrent before login"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by xwizzard on 2009-05-29
Ok, I have Ubuntu Server (AMD64) set up as a file and print server. I installed the ubuntu (GNOME) desktop and have several "desktop user" accounts setup to use the XDMCP remote login if needed. All the users can access the files and printers with Windows via SAMBA sharing, or through the XDMCP login. In short, file and printer sharing are enabled before any session login actions take place.

I would like to do the same thing with a torrent program that I have in place with the file and print sharing. I have Transmission configured to auto-load torrent files from a private, admin-only folder; and deposit the download/seeding files to a shared folder. Currently the program does what I want, but requires an admin login locally or via XDMCP.

Is there some way to start and run Transmission during boot, before login?

---

### Post by MrWES on 2009-05-29
> **xwizzard said:**
> Ok, I have Ubuntu Server (AMD64) set up as a file and print server. I installed the ubuntu (GNOME) desktop and have several "desktop user" accounts setup to use the XDMCP remote login if needed. All the users can access the files and printers with Windows via SAMBA sharing, or through the XDMCP login. In short, file and printer sharing are enabled before any session login actions take place.

I would like to do the same thing with a torrent program that I have in place with the file and print sharing. I have Transmission configured to auto-load torrent files from a private, admin-only folder; and deposit the download/seeding files to a shared folder. Currently the program does what I want, but requires an admin login locally or via XDMCP.

Is there some way to start and run Transmission during boot, before login?

Check out the transmission web site and run it as daemon (service). There are links to scripts to start it all up a boot time:
[http://www.transmissionbt.com/]("http://www.transmissionbt.com/")
[http://trac.transmissionbt.com/wiki]("http://trac.transmissionbt.com/wiki")

You might also be interested in rtorrent, which in my opinion, has better ratio management and less overhead. I installed the subversion copy.
[http://libtorrent.rakshasa.no/]("http://libtorrent.rakshasa.no/")
[http://howtoforge.org/compile_rtorrent_from_svn_ubuntu]("http://howtoforge.org/compile_rtorrent_from_svn_ubuntu")
rtorrent is what I run on my headless server and I'm very happy with it.

~Bill

---

### Post by xwizzard on 2009-05-29
Thanks fo the advice! I will look into both.

---

