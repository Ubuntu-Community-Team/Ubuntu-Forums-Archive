---
title: "your preferred BitTorrent application?"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-04
Which of the many BitTorrent apps do you prefer?

What are the pros and cons of a torrent app installed on your machine and one that's a plug-in for Firefox?

I've got (at least) 4 torrent apps installed on my computer - Bittornado Client, BitTorrent Download Client, KGet, Transmission BitTorrent Client. For some reason, KGet is my default app, so that's the only one I've used so far.

I'm a little frustrated with KGet, as there doesn't seem to be a recovery option for a file if I disconnect from the internet for some reason (e.g. when a restart is needed after a general system update).

On Windows, I was used to using uTorrent, which I found to be very user-friendly and I liked the search facility from within it (something also that KGet seems to lack).

To get the search facility, should I consider a Firefox Add-on, such as Torrent Finder Toolbar or FireTorrent?

---

### Post by sandyd on 2009-10-04
ktorrent?
vuze?
transmision?
deluge?

ktorrenthas a search function built in.

plugins offer less funtionality. for example, you might not be able to view the detailed properties such as seeders/leechers, edit trackers, that kind of stuff.

utorrent can run on linux (wine)

---

### Post by ankspo71 on 2009-10-04
Hi,

I just use transmission because it is the default torrent app in Ubuntu. It works fine for what I download.... iso's for linux.

As far as searching for your torrents go, have a look these sites:
[http://www.usniff.com/](http://www.usniff.com/)
[http://www.nowtorrents.com/](http://www.nowtorrents.com/) 
[http://www.go-torrent.com/index.php](http://www.go-torrent.com/index.php)
For linux distro torrents only:
[http://linuxtracker.org/](http://linuxtracker.org/)
[http://distrowatch.com/](http://distrowatch.com/)

They work great, but I'm like you, I would much rather prefer using a single app for searching instead of having to actually visit each site to see who has the most seeders. 
Hope this helps.
James

---

### Post by nhasian on 2009-10-04
if you like utorrent in windows (which by the way works fine with wine) then you would like the program deluge as the layout is very similar.

Personally i just stick with transmission that comes default in ubuntu as it does everything i need it to do, plus i dont use p2p very often.

---

### Post by falconindy on 2009-10-04
Former uTorrent user here. There's people using it through Wine if you were interested in that. I wasn't.

I'm using Deluge now, and I've been very satisfied with it. A lot of its power comes from plugins, which makes it really small and fast if you don't desire the extra functionality, but also robust if you decide to install plugins. Like many other linux torrent clients, it comes with a web UI, but also gives you the option to control it via IMs through on Jabber. Also, the first thing I noticed about Deluge is that it looks an awful lot like uTorrent as far as the interface.

I'd opt to stay away from adding plugins like torrent downloaders to Firefox. A torrent application can clearly stand on its own, and running it as a plugin to another program seems like you're just asking to slow down FF. In addition, you're likely missing out on remote accessibility via a webUI or other methods.

Prior to Deluge, I used Transmission, qBitTorrent, and torrentflux. Wasn't entirely satisfied with any of them.

---

### Post by jmszr on 2009-10-04
Roger Allot,

I prefer Deluge, for the reasons falconindy gave, but Transmission is also good for some puposes.

Here is a summary of various Ubuntu bittorrent clients and their features: [http://www.ubuntugeek.com/list-of-bittorrent-clients-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-bittorrent-clients-available-in-ubuntu.html)

---

### Post by starcannon on 2009-10-04
I use Transmission 1.75 from the ppa's.

---

### Post by tophatandy on 2009-10-04
I use transmission as that is what i have on my mac and found to be the most powerfull. Its simple too.

---

### Post by wojox on 2009-10-04
Deluge: [http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by Ingvar G. on 2009-10-04
I use Deluge, simple but poweful. Good luck with seeding!

---

### Post by ibutho on 2009-10-04
In order:
QBittorrent
Ktorrent
Deluge
Transmission

---

### Post by Roger Allott on 2009-10-04
Many thanks to all. I decided to try Deluge, and I like it. However, I now need to make it my default app for torrent files. Could someone please tell me how to do that?

---

### Post by falconindy on 2009-10-04
Right click on any .torrent file, and go to the "Open With" tab to manage the default app for that file type.

---

### Post by credobyte on 2009-10-04
Deluge should make itself as the default application for .torrent files, automatically. If not, right click on a torrent file, select Properties and browse to Open With tab.

---

### Post by fela on 2009-10-04
torrentflux on my server
ktorrent or transmission-qt on my desktop

---

### Post by Silent Warrior on 2009-10-04
As I dual-desk 8) on my laptop (Gnome + KDE4), KTorrent has its charm - in KDE, there's a panel-applet that runs the app without my interference, and... Well, it just seems to be the least amount of bother to use across desks at the time of this writing. And it works. Sure, any of the others work fine, there's no doubt in my mind. I've had good times with Transmission, Deluge, Azureus/Vuze (running that on my Windows-machine because I'm too lazy to change it, an' my CPU has the oomph to spare), BitComet...

---

### Post by misfitpierce on 2009-10-04
I use Transmission and not because its the default torrent client... Even when it was not the default in Ubuntu I still ran Transmission. Transmission is just the best to me and has been for a long time.

---

### Post by Roger Allott on 2009-10-04
> **credobyte said:**
> Deluge should make itself as the default application for .torrent files, automatically. If not, right click on a torrent file, select Properties and browse to Open With tab.

Thanks. I've done that and indeed any torrent I d/l will open in Deluge now when I open it. However, when I'm downloading a torrent from the web, the dialog box asks me what I want done with it and the default is to open with Transmission. At the moment, I'm therefore saving the torrent to a temp area, then having to open the torrent from the file browser.

---

### Post by credobyte on 2009-10-04
> **Roger Allott said:**
> Thanks. I've done that and indeed any torrent I d/l will open in Deluge now when I open it. However, when I'm downloading a torrent from the web, the dialog box asks me what I want done with it and the default is to open with Transmission. At the moment, I'm therefore saving the torrent to a temp area, then having to open the torrent from the file browser.

Remove Transmission :) It's an outdated version anyway ( unless you've updated it @ PPA ).

---

