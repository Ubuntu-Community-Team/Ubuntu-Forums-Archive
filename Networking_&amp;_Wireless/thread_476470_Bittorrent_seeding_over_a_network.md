---
title: "Bittorrent: seeding over a network"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by thatcrazycommie on 2007-06-17
I've just switched from Windows to Ubuntu. I still have it set up to dual boot, but, assuming I can get everything working, I'd like to make that change more or less permanent. Now, I'm a member of a bittorrent community that has strict ratio requirements and requires a lot of seeding. The bittorrent client I am running in both OSes is Azureus.

My problem is that, in Windows, it let me seed files over my network. That is to say, I connect to my downstairs computer's share folder, configure it as a network drive, then aim Azureus there. In Ubuntu, I can connect to that share, and listen to my music and watch my movies and everything, but it doesn't think of it as an actual drive, and when I load a torrent into Azureus, it doesn't seem to "see" the share folder as a viable place to save the data, like it does in Windows.

Can I make a Windows share (which I *have* successfully connected to) be read as a drive, or as just a regular folder, so that Azureus will see it and let me seed the data that's there? That would be awesome.

---

### Post by oursin on 2007-06-28
Have the same problem. Running on VMware and want to download my torrent to a network drive on my winxp. I'm able to write to the share but the downloads in my torrentclient does not start when i choose the share as my download folder. Is this a problem with torrent (on linux)  in general og could it be my client. Using Opera but tried torrentflux as well

---

### Post by t4thfavor on 2007-06-28
you can mount a windows share under a folder on your pc. Just do a bit of research on the mount command, or under places --> Connect to Server. Set the share up that way and I believe it will mount somewhere under a local folder just do a search for it.

Or you could always put ubuntu on the other PC as well :)

---

### Post by oursin on 2007-06-28
used the path smb://user@192.168.1.50/downloads

Worked great. Thaks!

---

