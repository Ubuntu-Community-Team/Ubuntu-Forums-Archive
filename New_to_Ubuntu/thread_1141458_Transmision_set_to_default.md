---
title: "Transmision set to default?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by monolux on 2009-04-28
How do I set transmission back to default?

---

### Post by hesjnet on 2009-04-28
[LIST][*]Find a torrent file and right click on it.[*]Choose properties[*]Choose tab "open with"[*]Choose Transmisson




[/LIST]

Hope this helps

---

### Post by lovinglinux on 2009-04-28
> **hesjnet said:**
> [LIST][*]Find a torrent file and right click on it.[*]Choose properties[*]Choose tab "open with"[*]Choose Transmisson




[/LIST]

Hope this helps

If you want to set Transmission to open torrents by default, then do what is explained above. Please notice that you should find a torrent file using the file manager, not Transmission itself, so you can make it default for the system.

If you want to go back to Transmission default settings (like when you first installed it, then close it,  delete the folder ./transmission in your home directory and restart Transmission. Please notice that this will remove the current torrents being downloaded, but not the files downloaded.

---

### Post by lovinglinux on 2009-04-28
I forgot to mention, that you might also need to open Firefox Preferences, then select the "Applications Tab", then select "BitTorrent seed file" in the content column, then "Use Transmission BitTorrrent..." in the action column.

This will allow you to click a torrent link on a web site and open it automatically with Transmission.

---

