---
title: "Transmission hangs, then won't restart"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by adamogardner on 2010-12-29
Since yesterday, it's been going dark while attempting to download a torrent, and effecting my computer's speed (I was using firefox).  After I force close, Transmission won't reopen because it is still running.  After killing the PID and restarting the computer, I'm having the same problem.  Other than reinstall, or find another package (suggestions?) what is going on and what can I do?
Thanks

---

### Post by producer on 2011-01-16
I have the exact same problem and I think it's something to do with having loaded a torrent that was a trojan, but I remember last time I edited the configuration of the torrents deleting only the most recent one. and it started working again.  Can't remember if I had to restart the computer, but now I've forgotten where the directory is for the configuration.  So I'm stuck again.  If anybody can help it would be appreciated.

---

### Post by CCoder on 2011-01-16
Just use Deluge or BitTorrent instead of Transmission. It's much more capable than Tra~.

---

### Post by CCoder on 2011-01-16
double post - deleted.

---

### Post by producer on 2011-01-16
GOT IT!  It's in my home directory,  .config  then transmission.  There are sub directories for resume  and  torrents .  Going into each of these and deleting the latest addition restores functionality.  When transmission stops in this manner, it means that you've tried to download a "poison torrent" (as near as I can figure out).  OR at least a torrent that is not working for whatever reason.  Once it's gone in both these directories, I find I an back to business as usual, except that I don't get that particular torrent.
I have yet to try Deluge or Bit Torrent,  I might at some point, but I'll do a bit more research before jumping in.

---

