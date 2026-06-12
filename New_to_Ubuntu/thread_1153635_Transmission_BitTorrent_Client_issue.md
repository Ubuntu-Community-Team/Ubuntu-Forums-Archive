---
title: "Transmission BitTorrent Client issue"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by RagnorakTres on 2009-05-09
I'm trying to use the Transmission BitTorrent Client to (this is kind of obvious, but whatever) download a .torrent file. Unfortunately, it will not download, and the error returned is "Data not fully available." I did a Google for "Transmission BitTorrent data not fully available" and found a thread on another site that led me to something called a "nightly" that supposedly fixes the problem. But now there's a new problem: the file was downloaded as a Macintosh disc image file (.dmg) for some reason. So I obviously can't install that, unless you guys have some way of changing the file type.  I'd like to know several things: is there a simpler way of fixing this issue with Transmission? If there is, what is it, where is it, and how do I implement it? If not, what do I do to translate the file into a file that I can install?

---

### Post by tjwoosta on 2009-05-09
When you download a .torrent transmission doesn't choose what the filetype is, the person who made the torrent does.  If you get a .dmg file its because thats what the uploader uploaded.

What are you trying to download?

here are some links that might help

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/56440-how-install-open-dmg-file-fc4.html]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/56440-how-install-open-dmg-file-fc4.html")

[http://baghira.sourceforge.net/dmg.htm]("http://baghira.sourceforge.net/dmg.htm")

---

### Post by lovinglinux on 2009-05-09
@ tjwoosta

The dmg file wasn't downloaded by the torrent client, since the client isn't working. It was actually a "nightly build" of Transmission itself, that the OP downloaded from some web site.


@ RagnorakTres

A "[nightly build](http://en.wikipedia.org/wiki/Nightly_build)" is the most recent version of a software, that is usually updated overnight, while it is being developed or improved, so it might have the latest fix. The problem is that you have downloaded an [Apple Disk Image](http://en.wikipedia.org/wiki/.dmg). It is the equivalent of an ISO file, used to burn a CD/DVD. 

Is not recommended to download applications from sites you don't know. The most secure way of installing software for Ubuntu is from the official repositories. Have you updated your system lately? Updates might fix some problems.

Anyway, if you can't find a fix with regular updates, then you could try using the most recent .deb release from other sources like GetDeb web site. A .deb file is the most simple method of installing applications instead of using the repositories. It is the equivalent of the exe in Windows. All you have to do is double click on it to install. You can get the newest release of Transmission [here](http://www.getdeb.net/app/Transmission). It was updated 2 days ago.

I personally would like to recommend using Deluge instead of Transmission. I has several additional features, is easy to configure and has a nice interface. Is the best torrent client in my opinion. Deluge is in the repositories, but you can get version 1.1.6 from [here](http://www.getdeb.net/app/Deluge). Deluge also provide a repository for itself, with which you can get the latest version and keep it update with future releases. The PPA repository is available at [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

If you don't know how to use a PPA repository, then read this:

[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by hobo14 on 2009-05-09
Assuming you mean you are using Transmission and a .torrent file to download some other file, not actually downloading the .torrent file as you said?

"Data not available" for a torrent sounds like there is simply not enough seeders.  All the leechers are sharing between themselves, but there is part of the file that none of them have.

If this is the case, no upgrade is going to fix the problem, you need a seeder.

---

### Post by tjwoosta on 2009-05-09
> **lovinglinux said:**
> @ tjwoosta

The dmg file wasn't downloaded by the torrent client, since the client isn't working. It was actually a "nightly build" of Transmission itself, that the OP downloaded from some web site.


ahh, ok I see 

That makes sense now, I guess I was too tired last night.

---

### Post by RagnorakTres on 2009-05-09
Well, I installed the Deluge client and it seems to work much better than the Transmission did, sensing that my Dad's firewall is the thing blocking incoming transmissions and actually telling me that a firewall is in the way. Now I just have to convince Dad to open his firewall for me...which probably isn't going to happen. Thanks for all your help!

---

