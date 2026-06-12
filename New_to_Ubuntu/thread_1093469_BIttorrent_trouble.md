---
title: "BIttorrent trouble"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by MikesGuitar on 2009-03-11
Is Transmission a good bt program or should I look else where? I find it to be a little glitchy. Also almost all of my torrents download at a snails pace, is there anyway to ensure that I am getting all I can out of bt? Thanks yall

---

### Post by kanikilu on 2009-03-11
Deluge seems to be pretty popular...

---

### Post by cb951303 on 2009-03-11
transmission doesn't support queuing and DHT.
it's a good client though I have better download rates with deluge

---

### Post by MikesGuitar on 2009-03-11
Where would I find Deluge, add/remove or package manager?

---

### Post by KIAaze on 2009-03-11
I'm not a big torrent user, but I used gnome-btdownload recently (which is what comes up by default if you haven't set any torrent app) and it worked well.

Others:
-Ktorrent
-Azureus (bloated)

edit:
> **MikesGuitar said:**
> Where would I find Deluge, add/remove or package manager?
```
sudo apt-get install deluge-torrent
```
[http://packages.ubuntu.com/intrepid/deluge-torrent](http://packages.ubuntu.com/intrepid/deluge-torrent)

---

### Post by kanikilu on 2009-03-11
> **MikesGuitar said:**
> Where would I find Deluge, add/remove or package manager? [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

Or ```
sudo apt-get install deluge-torrent
``` Although to be honest I'm not sure what version that is...I don't use it.

---

### Post by MikesGuitar on 2009-03-11
Right on, thanks guys!

---

### Post by MikesGuitar on 2009-03-11
One more thing.... anybody know a good bt site? i tried torrentz.com, and btjunkie (which is pretty good), but nine times out of ten I get a bogus torrent that wont even start, or it is locked. Is there a better site where I can search torrent within it and not get redirected to sites with porn all over it? (most of my dling is done in class haha)

---

### Post by KIAaze on 2009-03-11
That depends. What do you plan to download? :p

[http://beta.legaltorrents.com/](http://beta.legaltorrents.com/)
[http://www.legittorrents.info/](http://www.legittorrents.info/)
[http://linuxtracker.org/](http://linuxtracker.org/)
[http://torrent.ubuntu.com/](http://torrent.ubuntu.com/)

(but for distro isos, it's best to get them on the official disto site of course)

I'm not sure if the moderators are ok with promoting torrent sites hosting illegal material.:rolleyes:
Maybe you should just run firefox with noscript and block all images... or google...

Hint: There's a very famous torrent site currently being "promoted" in the news. ^^

---

### Post by MikesGuitar on 2009-03-11
Just looking to download music

---

### Post by kanikilu on 2009-03-11
> **MikesGuitar said:**
> Just looking to download music Legal torrent of SXSW 2009 music: [http://sites.google.com/site/sxsw2009torrent/](http://sites.google.com/site/sxsw2009torrent/)

---

### Post by lovinglinux on 2009-03-11
> **kanikilu said:**
> [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

Or ```
sudo apt-get install deluge-torrent
``` Although to be honest I'm not sure what version that is...I don't use it.

It is version  1.1.4, which is the latest release. You can also download the newest deb files from Deluge web site at [http://deluge-torrent.org/](http://deluge-torrent.org/)

> **MikesGuitar said:**
> One more thing.... anybody know a good bt site? i tried torrentz.com, and btjunkie (which is pretty good), but nine times out of ten I get a bogus torrent that wont even start, or it is locked. Is there a better site where I can search torrent within it and not get redirected to sites with porn all over it? (most of my dling is done in class haha)

What do you mean by locked? You need to configure your torrent application properly, your router to port-forward the required port and your firewall to allow traffic. Since you are downloading from class, I guess the school network is blocking p2p traffic, which is pretty common and fair. Using your school network resources for personal downloads is not a good move. Downloading illegal files is even worse. I'm not judging you or presuming this is your intent, since torrents can be a very useful tool inside a classroom and there are lots of legal torrents out there. But you could get into a lot of trouble if you do and also put your school in a difficult situation (read torrent news about this). 

Torrentz.com is just a search engine (a pretty good one). The search results  shows several popular torrent sites from where you can download the same torrent. Some sites listed by Torrentz.com are better than others. Is up to you to decide. Nevertheless, most torrent sites require registered accounts to upload torrents. This means that you should check the uploader before downloading. Torrentz.com display a green icon next to "trusted" uploaders.

---

