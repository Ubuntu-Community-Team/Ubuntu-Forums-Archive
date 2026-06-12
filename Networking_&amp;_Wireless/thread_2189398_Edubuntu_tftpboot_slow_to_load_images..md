---
title: "Edubuntu tftpboot slow to load images."
date: 2013-11-22
forum: Networking &amp; Wireless
---

### Post by knigits on 2013-11-22
G'day everyone.

I tested the Edubuntu 13.10 LTSP Live DVD on my desktop PC and my thin clients booted very fast (under a minute).  However...

I installed Edubuntu 13.10 on my IBM eServer x3500 and my thin clients now boot extremely slowly (almost six minutes).  By removing the splash screen options from pxelinux.cfg/default, I can see that vmlinuz-3.11.0-12-generic and initrd.img-3.11.0-12-generic are loading extremely slowly.  Once they've loaded, however, the client finishes booting in a matter of seconds.

The server has six gigabytes of RAM, SAS hard drives and two gigabit ethernet ports.  Can anyone think of a reason why tftpboot would be transferring those two images to thin clients at the speed of a snail in molasses?

---

### Post by knigits on 2013-11-22
After more testing, I've discovered that if I plug a thin client into the same switch as the server, it boots in under thirty seconds.  The other thin clients are connected via Netcomm NP504 ethernet-over-powerline adapters, and this seems to cause the netboot to be extremely slow.

---

