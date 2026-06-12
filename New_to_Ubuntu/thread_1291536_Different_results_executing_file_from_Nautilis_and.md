---
title: "Different results executing file from Nautilis and Terminal"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-14
When I run this file ** /home/username/torrents/movie.torrent** from Nautilis, it opens with my default bit-torrent app (bit tornado).

When I run it from the command line in Terminal, it tells me "*Permission denied*" (and I'm using it as the same user.

When I run it as **Sudo** it tells me [I]sudo: "/home/username/torrents/movie.torrent: command not found"

[/I]If I tick the *Allow executing file as a program* in Nautilis and run in Terminal, I get a bunch of funny output.

What gives?!

Do I need to tell it to open with Bit Tornado?

Can anybody help me with the command to do this? I wouldn't know:(

I'm trying to get the file to open in Gnome-Schedule 2.02 but need to enter the command.

---

### Post by tuxxy on 2009-10-14
If you want to launch the torrent using your terminal then you need to tell it to open the the torrent in Bit Tornado rather tahn just typing in the path to the torrent.  So use the command to launch Bit Tornado then space and the torrent filename.  I prefer to use Deluge so I would do this for example but you replace deluge with your client

```
cd /home/username/torrents/
```

```
deluge movie.torrent
```

---

### Post by smileyguy on 2009-10-14
Thanks:)

That worked in Terminal.

I assume I can just enter those two lines of code beneath eachother in the Gnome-Schedule interface under the TASK section. I'll go and test it.

---

### Post by tuxxy on 2009-10-14
Yes just enter the command as you did in terminal and it should be fine

---

