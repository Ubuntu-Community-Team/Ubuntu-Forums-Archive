---
title: "Looking for a better torrentclient"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-06-11
I've got a server running, currently with deluge + the webui. It is working pretty good, I can dump all the torrents in a folder which get's scanned by deluge and will process then from there. The only thing I'm missing is the option of automaticly moving completed torrents to a certain directory, and perhaps categories which can be predefined, movies, music etc. rtorrent seems pretty nice, but don't have the courage and knowledge yet to tackle installinging and configuring it.
Does anybody have any other options? I've tried Transmission a while ago on another PC but it seems to slow the pc down when there's alot of torrents active.

---

### Post by steeleyuk on 2009-06-11
Deluge can do both of those features you're looking for. Though I'm now sure if it can do it through the WebUI.

The categories are done using a plugin.

---

### Post by dvdhaar on 2009-06-11
> **steeleyuk said:**
> Deluge can do both of those features you're looking for. Though I'm now sure if it can do it through the WebUI.

The categories are done using a plugin.

Thanks for your reply. Could you point me to the plugin? I've seen some discussion in the deluge boards but haven't been able to find a place to download or install? On the other hand, if I can't control it via the webui or cli it's not very practical for me since the server is headless etc.

---

### Post by MrWES on 2009-06-11
> **dvdhaar said:**
> I've got a server running, currently with deluge + the webui. It is working pretty good, I can dump all the torrents in a folder which get's scanned by deluge and will process then from there. The only thing I'm missing is the option of automaticly moving completed torrents to a certain directory, and perhaps categories which can be predefined, movies, music etc. rtorrent seems pretty nice, but don't have the courage and knowledge yet to tackle installinging and configuring it.
Does anybody have any other options? I've tried Transmission a while ago on another PC but it seems to slow the pc down when there's alot of torrents active.

Definitely run rtorrent. I run the subversion edition on my headless server. It has ratio sharing. Here is a very good guide I followed and got it working first time out.

[http://howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron]("http://howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron")

Give me a shout if you need help.

Bill

---

### Post by Gen2ly on 2009-06-11
I know alot of people like ktorrent.  I haven't got to fully trying it out but it might have what you're looking for.

---

### Post by lovinglinux on 2009-06-11
> **dvdhaar said:**
> Thanks for your reply. Could you point me to the plugin? I've seen some discussion in the deluge boards but haven't been able to find a place to download or install? On the other hand, if I can't control it via the webui or cli it's not very practical for me since the server is headless etc.

Do you know Deluge also offers remote gtk? You can install the client on the local machine and connect to the headless server like you do with webui or cli. Is really very nice. You can control everything with it.

---

### Post by H2SO_four on 2009-06-11
Deluge works well, and has the auto move on completion feature in preferences>downloads.

---

### Post by powel212 on 2009-06-11
+1 Ktorrent

---

### Post by superprash2003 on 2009-06-12
+1 deluge

---

### Post by andrew.46 on 2009-06-12
Hi MrWes,

> **MrWES said:**
> Definitely run rtorrent. I run the subversion edition on my headless server. It has ratio sharing.

I have been meaning to get rtorrent going for some time and I will actually bite the bullet now I have a week or so off :-). Are there any special benefits from running the svn version, or is the release close enough?

Thanks for your trouble,

Andrew

---

### Post by hero1900 on 2009-06-12
try VUZE

---

### Post by MrWES on 2009-06-12
> **andrew.46 said:**
> Hi MrWes,



I have been meaning to get rtorrent going for some time and I will actually bite the bullet now I have a week or so off :-). Are there any special benefits from running the svn version, or is the release close enough?

Thanks for your trouble,

Andrew

Andrew, 
From what I've read and found out from hanging out in #rtorrent (freenode.net) is that the version in the repositories is very long in the tooth and the latest and greatest from subversion is very efficient and from what I've seen, reliable and stable. The additional advantage to using subversion is you can always update to the latest and greatest very easily with the svn up command. The additional suggestion I would have is to consider using a checkinstall make verus the plain make command. This will allow you to wrap everything up as a package and allow you to remove with the apt-get remove command.

[CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

I normally have rtorrent running with a screen session and drop .torrent files from my laptop to the watch folder on my server. Can't really get any easier :).

Bill

P.S. Oh...and I had never installed a subversion of anything, and I wanted to learn how -- hate not knowing :)

---

### Post by MrWES on 2009-06-12
> **hero1900 said:**
> try VUZE

VUZE runs from the command line on a server? I wasn't aware of that. IMHO, VUZE is a pig anyhow. Rtorrent will give you a lean and mean torrent client that'll keep taking .torrent files and respond with "... thank-you sir, may I have another?" (Alittle Animal House humour)

~Bill

---

### Post by andrew.46 on 2009-06-12
Hi MrWes,

> **MrWES said:**
> From what I've read and found out from hanging out in #rtorrent (freenode.net) is that the version in the repositories is very long in the tooth and the latest and greatest from subversion is very efficient and from what I've seen, reliable and stable. 

Thanks for that, I shall definitely give it a go then :-).

> Oh...and I had never installed a subversion of anything, and I wanted to learn how -- hate not knowing :)

Well there is a much neglected guide on these forums that I saw the other day:

Linux Basics: A gentle introduction to accessing 'svn' repositories
[http://ubuntuforums.org/showthread.php?t=1167578](http://ubuntuforums.org/showthread.php?t=1167578)

Written by a man who obviously spends too much time on these forums :-).

Andrew

---

### Post by MrWES on 2009-06-12
> **andrew.46 said:**
> 

Written by a man who obviously spends too much time on these forums :-).

Andrew

Hrmm..weird, seems to be the same writing style as the guy who wrote the guide for ABCDE :P

Bill

---

### Post by Gen2ly on 2009-06-13
> **andrew.46 said:**
> ...
I have been meaning to get rtorrent going for some time and I will actually bite the bullet now I have a week or so off :-). Are there any special benefits from running the svn version, or is the release close enough?

Thanks for your trouble,

Andrew

I likertorrent alot too.  Attached a config-file for any to use.

[Link]("http://www.archive.org/download/rtorrent.rc/rtorrent.rc.tgz")

---

### Post by andrew.46 on 2009-08-11
Hi Bill,

> **MrWES said:**
> Rtorrent will give you a lean and mean torrent client that'll keep taking .torrent files and respond with "... thank-you sir, may I have another?" (Alittle Animal House humour)

A quick note to say thanks for putting me on to rtorrent. After a great deal of procrastinating I finally installed this fine program and I am in the middle of downloading my first torrent. Not the most beautiful-looking program by any stretch of the imagination but it runs very, very fast and with great efficiency.

The stimulus for me to get it all going has been a change of plans with my isp which now has free uploads and free downloads between 0200 and 0800.

Happy seeding :-)

Andrew

---

