---
title: "How to speed up downloads"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by djmoore85 on 2008-05-31
Hey yall, been tryin to find a solution on download speeds, I have a connection that Ubuntu says is running at full speed but my download speeds for torrents using BitTorrent are horrible. How do I allocate more bandwidth or fix this issue? Thanks in advance

---

### Post by pytheas22 on 2008-05-31
Ubuntu shouldn't be doing anything to limit your connection speed.  Are you able to download other things at decent speeds (i.e. files from the Internet or ftp servers)?

A lot of ISPs try to block torrent connections; that's probably the problem.  If you try changing the ports that BitTorrent uses, you might have better luck.

---

### Post by damis648 on 2008-05-31
Well, bittorrent downloads are pretty much alot of the time slow. Try to find one with less leechers and more seeders.

---

### Post by kshane on 2008-05-31
There needs to be more how-to info out about torrents...  I avoid using any torrents for downloads.   I almost ALWAYS get better speeds without.  I have a good friend that swears by BitTorrent, but it never works for me as well as him.

Kevin

---

### Post by djmoore85 on 2008-05-31
Now how do I go about changing ports and such, or possibly randomizing them each time BitTorrent opens? When I open the BitTorrent program there seems to be just the download interface and no area to adjust settings or preferences. And yes it is only with torrents, and I do my best to find more seeders than leechers, so I am willing to give the port-switching a try

---

### Post by pytheas22 on 2008-05-31
I've never really used BitTorrent, but if it's the client that comes default with Ubuntu 7.10 and earlier, I recall it not having many options.  I'd recommend installing [Deluge]("http://deluge-torrent.org"), where you can easily change the ports under the Network tab of the preferences dialogue.  There's no guarantee that changing the ports will solve the problem, but it can't hurt to try.

You could also just call your ISP and ask if they do anything to hinder torrent traffic--just be warned that it might be against your terms of service to use torrents (I know from experience) and they'll threaten you if they find out you are, so it's best to not actually say that you're using them; just say you want to know, and remind them that there are plenty of legitimate things that you can share using torrents, like Ubuntu.

---

