---
title: "Suspend + Internet"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by PabloTortilla on 2009-05-29
I was wondering if it was possible to go into Suspend or Hibernate, and still be connected to the internet. Are there any add-ons or plugins to make this possible?

---

### Post by Volt9000 on 2009-05-29
I could be wrong, but I think the nature of your question is contradictory.

In Hibernate mode especially, the computer is powered OFF, so staying connected is not only impossible, but useless, as a computer that's off can't do anything.

Not sure about Standby-- AFAIK in Standby mode the computer has most devices turned off, except for RAM.

---

### Post by PabloTortilla on 2009-05-29
Well, what i want to do, is have torrents downloading, but make my laptop use as little power as possible. It's a wired connection. Is there anything that could make it appear off?

---

### Post by Hospadar on 2009-05-29
Short answer is no.  When you hibernate, the computer saves portions of RAM to disk and totally powers off, in suspend, a small amount of power is juiced through RAM to keep the data there viable, but otherwise the computer is basically totally powered off.

That said, you could switch to a lower power profile by doing a couple things:
-Set the screensave to power off the monitor when you arn't using it.
-I know kde has extensive power management options and profiles you can monkey with, I believe gnome has something similar
-use a torrent daemon (i.e. background process) so you can kill your graphics environment at night
--transmission, which comes default with ubuntu can be run as a daemon, you can kill your graphics environment with a command like "sudo /etc/init.d/gdm stop" (replace stop with start or restart for desired effect)

Alternatively, consider a low power server.  Nowadays you can get a little mini-itx/micro-atx mobo with integrated atom or via CPU for under a hundred bucks, add cheap hard drive, $40 or less power supply, ubuntu server install, and you've got a world class all-night-long bittorent and fileserver.  Also consider using an old machine or laptop for this purpose, they often have low power requirements and not much power is needed to serve a few files and run bittorent off the command line.

Further note, transmission, aforementioned bt client, has a great web interface built into it, if you do go the server route, it's a great way to easily manage your torrents remotely

---

### Post by Volt9000 on 2009-05-29
Then I would suggest setting up your laptop to turn off the screen after some time.

Also, I hear there's a great low-usage torrent client called rtorrent which will probably suit your needs, although be warned it's command-line.
There's a great article someone linked to, here:
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

