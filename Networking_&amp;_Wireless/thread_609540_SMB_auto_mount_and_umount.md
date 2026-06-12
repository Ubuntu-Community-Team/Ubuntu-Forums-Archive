---
title: "SMB auto mount and umount"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by brownrl on 2007-11-11
Beste,

A little question I hope...

Using laptop computer to connect to a desktop machine and mount some parts using Samba.

( videos, musics, etc... )

When I unplug the laptop from the network to go somewhere or when I turn off the server desktop. I get this behavior

[LIST]
[*]File Viewer becomes extremely slow ( stuck )
[*]Can't access the top level directory that contains the shares
[*]The share mount points themselves become unaccessible files instead of directories
[*]Umount does not work
[*]Smbumount does not work
[*]The desktop and gnome do a sort of reboot and I loose icons on the desktop
[*]mplayer does not want to play movies ( yes I know very odd something with direct draw )
[/LIST]

kill -9 the original smbmount process is not helping either...

Any ideas how I can get this stuff to auto umount when the network is detatched?

Thanks a ton in advance,
Rob

---

### Post by brownrl on 2007-12-03
BUMP!

I am also getting this with NFS sharing as well...

I literally have to do the Microsoft thing every day and reboot and kill X.

gnautilus more or less just doesn't work any more and no more desktop icons...

Also when it all is working does any one know why a large file transfers via wireless would completely freeze up nautilus? The router and the computer are about 3 meters from each other and the destination computer is wired.

Any ideas?

---

### Post by brownrl on 2007-12-03
Well,

To make things bareable:

I create a panel icon that does killall -9 nautilus.

This kills stuck nautili and thus things get rebooted sorta. Desktop icons and new nautili work.

Would like to know something better.

---

### Post by AlanRogers on 2007-12-03
Can you not make mount and umount shell scripts that you run when you're plugged into the network and before you unplug? Just thinking outside the box a little here; I can't actually tell you how to do it! :oops:

---

