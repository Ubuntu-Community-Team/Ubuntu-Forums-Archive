---
title: "Torrent crash my internet connection"
date: 2014-11-28
forum: Networking &amp; Wireless
---

### Post by alessandro-valentini-90 on 2014-11-28
Hi all, this is my first post.

I am experiencing  a strange problem with both Ubuntu (notebook) and Debian (file server): if I add a torrent to Transmission after some minutes my internet connection becomes  extremely slow, it remains up but even web pages timeout and torrent disconnects. After some minutes it recovers some peer and restart downloading leading to another lock. When this happens even the router UI is unreachable (but i can ping it) and when I stop torrent (or switch off Linux) it immediately loads the page. From DSL log the connection results stable.
This happen even with very few peers (only 5-10 ) and very slow speed (at most 40KB on a real 5-6Mb/s connection) so is not a problem of overloading or too many connections.

For example this morning I have only one torrent active (0b/s down and 10Kb/s up, only 1 peer connected) and connection results very slow.

There are (at least) two strange facts:
1- The slowdown seems to be caused by upload, ubuntu iso (with upload 0) will be downloaded at 450-500kB/s without any problem 
2- The same torrents with uTorrent on Windows will be downloaded at a reasonable speed (60-150kB with 5-10 peers) without causing sensible slowdown. So I don't think  is a router or ISP problem.

I have yet reset the router (Asus DSL-N55U), even with the so called "firmware dance" (factory rest, downgrade to original firmware, factory reset, double upgrade to last firware, facatory reset again). I'm using this router since february and I have this server downloading all the summer (assembled in July).

Debian seems to have the same behavior even with Deluge, but I have not tested it extensively, this evening I will try even Vuze and Deluge on my Thinkpad.

I have found bug reports since 2008 but no solution, sometimes the problem disappear after some upgrade.

Thank you in advance

---

