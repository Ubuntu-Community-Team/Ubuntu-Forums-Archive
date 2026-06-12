---
title: "Samba to xp 64 streaming issues"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by selari on 2007-02-09
I have a server running Edgy x86_64 and Samba 3.0.22.  I have a few shares set up and can access, read, write to them just fine from my OSX and XP 32bit computers.  However, when I try to stream a movie to my XP 64bit computer, after a few minutes the stream stops.  VLC says the input bitrate is -0k/s.  After the movie stops, I hit the stop button in VLC, start, and skip forward to where it stopped and it's fine again for the next few minutes.

There's nothing wrong with the movie file, when I restart playback it can read over the portion where it froze previously with no problems, as well as no other computers face the same problem as the XP 64 computer.  I don't think there's any problem with the XP 64 computer, because I can copy the movie to an XP 32 computer, share it, and it streams without incident.  VLC isn't to blame either, as I've tried Windows Media Player.  Foobar2000 also complains when I stream music.

My smb.conf socket options:
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

Anyone else have the same problems?

---

