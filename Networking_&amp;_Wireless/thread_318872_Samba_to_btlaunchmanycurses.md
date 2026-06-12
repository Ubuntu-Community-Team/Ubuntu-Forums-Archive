---
title: "Samba to btlaunchmanycurses"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by pixtor on 2006-12-14
Hello everybody!

I've got Ubuntu 6.06 Server running on a 386 kernel and AMD K6-2.
I've got samba set up on it and I'm using btlaunchmanycurses as a bittorrent client.
My problem is this:
I download a .torrent file and send it to my torrent-folder on the server through samba. Then btlaunchmanycurses gives me an "**warning** xxyyzz.torrent has errors" -error. 
However, when I FTP the .torrentfile; everything works great!

Any clues?

EDIT: Hmm.. it seems it could be a permissions-error, as I started the client with my own user-account and transfered the file using my sambamount-account. However... I FTP:ed with the sambamount-account too :P..hmm
Anyway, when I start the client with sudo, all's good. Even samba-transfered torrent-files.

---

