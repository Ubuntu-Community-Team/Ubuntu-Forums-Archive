---
title: "Deluge won't execute"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by malfist on 2007-06-18
I've been using Deluge for several weeks without a hitch, I'd even set Firefox to auto-open deluge when downloading torrent files. Yesterday, I tried to download a torrent and it did nothing. I pondered it, downloaded it again, still no deluge. Then I launch it from the Applications -> Internet -> Deluge and nothing happens.
I then reinstall it, still nothing. Then I launch it from commandline and this is what I get:
> 
jerome@jerome-desktop:~$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Torrent Size 891118714.0
Available Space 12496855040
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)

Anyone know how to fix this? I've had to go back to Azureus and that's no fun.

---

### Post by charleseddy on 2007-06-18
This is probably a deluge bug.  I would go to deluge and let them know, as we aren't deluge programmers so can't help much.

---

### Post by Reb on 2007-06-19
Remove ~/.config/deluge/persistent.state as a temporary fix.  Until deluge improves (and svn apparently is) I just use uTorrent with wine, it's very simple.

---

### Post by malfist on 2007-06-19
That's what they told me over in the deluge forums, remove it and svn the newest version.

---

### Post by BeauBobbitt on 2007-09-10
I had been using Deluge until the last set of updates. Now, it will not execute.

I had been using KTorrent until the last updates.  Now IT will not execute.

Does this combination help any of you guys who know this stuff - which does not include me?     Have PhD but lost here.

PS:  Azureus still works but I want to get away from it..

---

