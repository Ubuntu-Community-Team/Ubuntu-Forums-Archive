---
title: "BitTornado."
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by Roasted on 2006-08-06
Two things.

First of all, one of my torrents gave me this error. The other 3 torrents I started at the same time were fine. Why?:

BitTorrent T-0.3.13 (BitTornado)
OS: linux2
Python version: 2.4.3 (#2, Apr 27 2006, 14:43:5
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)]
wxWindows version: 2.6.1.2pre

Traceback (most recent call last):
File "/usr/bin/btdownloadgui", line 2325, in _next
savedas = dow.saveAs(choosefile, d.newpath)
File "/usr/lib/python2.4/site-packages/BitTornado/download_bt1.py", line 407, in saveAs
if path.exists(path.join(file, x['path'][0])):
File "/usr/lib/python2.4/posixpath.py", line 65, in join
path += '/' + b
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe2 in position 30: ordinal not in range(12


Secondly, I can't get anything better than a yellow dot for any torrents. I'm on cable, and right now I've got 5 torrents running. Four are transferring at 0/kb second, one is transferring at 2/kb second. Why? I set my ports JUST like portforwarding said to. I have screen shots of how it should look and everything. I'm seriously stumped. :sad:

---

### Post by sitedesign on 2006-08-07
Not sure how to solve your problem with that package but I am using torrentflux on my Ubuntu box and can access it via a web browser from my network or from outside (work etc) using portforwarding for the web interface.

Very smart system.
[http://www.torrentflux.com/](http://www.torrentflux.com/)

---

### Post by Roasted on 2006-08-07
I'll try it later. So far I've used 2 torrent programs, both with the same trouble.

On Bittornado I went into preferences and chose "force green icon if firewalled." I did, and it turned green.

Somehow, I'm firewalled. But how? How can I fix this? Somebody has to know...

---

### Post by Roasted on 2006-08-08
weeeeeeeeeeeeeeeeeeeee

---

### Post by sitedesign on 2006-08-08
did torrentflux work for you then!

---

### Post by Roasted on 2006-08-08
No I didn't try it. There's no reason for me to try it. There's got to be a reason that Azureus and BitTornado DON'T work. There has to be a solution. And with the nature of this forum with somebody always knowing something, I'm quite stunned that I haven't gotten an answer yet. But oh well, I'll keep trying!! 

*livin life 5 kb/second at a time* :(

---

