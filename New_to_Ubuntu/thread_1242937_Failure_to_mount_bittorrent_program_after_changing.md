---
title: "Failure to mount bittorrent program after changing ports"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by sebjob on 2009-08-17
Hi Hope all is well.

I am contacting you regarding the failure to re-open program after changing ports , which I run in EasyPeasy. Due to great advice here and on other pages, things went well when dealing with ports and firewall and to open them to get up the downloading speed.

The problem arised when I changed the port in the last page of bittorrent client, on my own initiative and experiment to get up the download speed. I added first one port, second time alike, which I had opened for firewall and forwarded. When I for the third time added with a regular port, number 80, the program immediately shut down by itself. Several times I tried to re-open it with no success; it only comes up the icon and a message that it is loading, but the message closes down and the program not loaded. Deleted and re-installed the program with no change.

Hope that you are able to help me with this
regards

---

### Post by zerhacke on 2009-08-17
Not really sure if it's the port program or the torrent program, but there's a way to check.

In a terminal type

sudo apt-get --purge remove bittorrentprogramname

And hit enter.  Then reinstall the program.  This will write all new config files.

If it doesn't work, then torrent was not the problem.

---

### Post by sebjob on 2009-08-17
thank you kindly. found out how to solve it. located the settings file for the program through the terminal, and then deleted it. then I deleted and reinstalled the program as you said. after that it mounted and works. thank you

---

