---
title: "Adding external storage"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by .Maleficus. on 2009-06-14
Here's the situation.  My current torrent slave is a pretty decent box, save for the 40GB hard drive.  The limited space is forcing me to remove torrents that I'd rather leave seeding so I can make space for new ones.  My setup is Arch + screen + rtorrent.  My rtorrent is watching the '~/torrents' directory, and my session directory is in '~/torrents/.session'.  My current 'torrents' directory has quite a few torrents being seeded, so I'd rather not move stuff around.

Moving on.  Today, I bought a Seagate 1.5TB external drive as addon storage.  It's currently mounted on '/mnt/external' with ntfs-3g so I have read/write as my user (wouldn't do much good otherwise).  What I want to do is eventually migrate all my data to that drive and leave the system's drive as just that, a system drive.  I was thinking that I could make a symbolic link to '/mnt/external/torrents' with the '~/torrents' directory, but would that work, with files in both directories?  Would I be better off moving all of the data to the drive and then doing a symlink?  Or scratching the symlink all together and just editing the .rtorrent.rc?

Normally I would just go ahead and try something out, but I've only got USB 1.1 on my box and I don't want to waste a day transferring stuff that doesn't need it.  I also don't want to lose seed time.

Thanks guys.

---

### Post by tarps87 on 2009-06-17
> **.Maleficus. said:**
> ...I was thinking that I could make a symbolic link to '/mnt/external/torrents' with the '~/torrents' directory, but would that work, with files in both directories?  Would I be better off moving all of the data to the drive and then doing a symlink?  Or scratching the symlink all together and just editing the .rtorrent.rc?...

From what I have tried I don't believe a symbolic link will work the way you want it to, a solution may be to point your torrent program to /mnt/external/torrents and then symbolic link the context of the ~/torrents folder e.g.

ls -s ~/torrents/* /mnt/external/torrents

---

### Post by LewRockwell on 2009-06-17
as far as data transfer is concerned, if it were my project I would open things up and make the fastest physical connection possible with the equipment I had on hand.

in my case I could just grab some loose components and lay them out on the work surface, connecting everything as necessary to have power, mobo, and the drives necessary to complete the transfer.

here, we have another reason why it's a good idea for the technician and the hobbyist to have some additional components on hand, if at all possible.
(and with all the machines being discarded this should be a simple task)

as always, your mileage may vary.

---

