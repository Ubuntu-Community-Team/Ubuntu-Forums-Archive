---
title: "rtorrent choose files help"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Syndacate on 2009-11-16
Hey,

If in a torrent file, there's two files being tracked, say like:
distro1.iso
distro1_x64.iso

And I only want the x64 version, is there any way to stop it from downloading the 32 bit image?  I know with regular (GUI) torrent programs you can simply check which files in the torrent to download, but how can you do that in rtorrent?  I tried hitting "right" arrow, going to "File Info" and turning "File Priority" to "off" by hitting space bar, but it still downloaded everything.  I've searched high and low and simply can't get my point across to the search in order to get an answer for what I'm looking for.

Anybody know how to do what I'd like to do?

Thanks in advance :) !!

- Greg

---

### Post by mobilediesel on 2009-11-17
> **Syndacate said:**
> Hey,

If in a torrent file, there's two files being tracked, say like:
distro1.iso
distro1_x64.iso

And I only want the x64 version, is there any way to stop it from downloading the 32 bit image?  I know with regular (GUI) torrent programs you can simply check which files in the torrent to download, but how can you do that in rtorrent?  I tried hitting "right" arrow, going to "File Info" and turning "File Priority" to "off" by hitting space bar, but it still downloaded everything.  I've searched high and low and simply can't get my point across to the search in order to get an answer for what I'm looking for.

Anybody know how to do what I'd like to do?

Thanks in advance :) !!

- Greg

rTorrent doesn't have the capability to only download certain files in a torrent, it's all or none. Changing the priority only tells it which file to concentrate its attention on.

---

### Post by fromthehill on 2009-11-17
> **mobilediesel said:**
> rTorrent doesn't have the capability to only download certain files in a torrent, it's all or none. Changing the priority only tells it which file to concentrate its attention on.
you can change the priority to 'off'

when in rtorrent select the torrent file
press 'right'
select 'file list'
press 'right'
select the file you want
press 'space' until 'off' appears (usually the first time)

[IMG][IMG]http://i35.tinypic.com/2il0qac.png[/IMG][/IMG]

sometimes a part of the beginning or the end of a deselected file gets downloaded because it shares a block with the file above or beneath it, but that's no different with other torrent clients

---

### Post by mobilediesel on 2009-11-17
> **fromthehill said:**
> you can change the priority to 'off'

when in rtorrent select the torrent file
press 'right'
select 'file list'
press 'right'
select the file you want
press 'space' until 'off' appears (usually the first time)

sometimes a part of the beginning or the end of a deselected file gets downloaded because it shares a block with the file above or beneath it, but that's no different with other torrent clients

Ah, I found more info on that. I totally didn't know rtorrent could do that!
There was a [bug report]("http://libtorrent.rakshasa.no/ticket/1120") filed on it still downloading files set to "off" but they said, just like you did, that it's because of chunks shared between the files.

---

### Post by fromthehill on 2009-11-17
> **mobilediesel said:**
> Ah, I found more info on that. I totally didn't know rtorrent could do that!
There was a [bug report]("http://libtorrent.rakshasa.no/ticket/1120") filed on it still downloading files set to "off" but they said, just like you did, that it's because of chunks shared between the files.

the poster in the bug report said it were all 700MB files
but that was like 2 years ago. so It should be fixed by now
I use the newest version without any problems

edit: now I see why my server's hdd has so much space used :D
I think it's time to stop the ridiculously large torrent I made a screenshot of
64GB downloaded and 166GB uploaded really is enough
glad my isp doesn't have download limits :P

---

### Post by mobilediesel on 2009-11-17
> **fromthehill said:**
> the poster in the bug report said it were all 700MB files
but that was like 2 years ago. so It should be fixed by now
I use the newest version without any problems

edit: now I see why my server's hdd has so much space used :D
I think it's time to stop the ridiculously large torrent I made a screenshot of
64GB downloaded and 166GB uploaded really is enough
glad my isp doesn't have download limits :P

yeah that bug report is positively ancient in internet years.

geez, I only got a 20GB drive on my current system. Trying to afford a NAS to install rTorrent on. Then I can turn the computers off while stuff downloads/seeds.

---

### Post by Syndacate on 2009-11-20
Yeah, thanks for the responses, sorry for the long reply.

If you look at my original post you'll see that I've done that, it's simply that with this one torrent there was like 10 versions in there and they all were seemingly downloaded although all but one was set to "off."  I'm not sure if that's a case of chunks overlapping files or not..  Either way, when you turn files' priority to "off" - the total download size doesn't appear to change.

Thanks for the answers thus far.

---

